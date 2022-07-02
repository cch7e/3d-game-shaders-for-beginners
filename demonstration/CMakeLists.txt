cmake_minimum_required(VERSION 3.12)

project(3d_game_shaders_for_beginners
    VERSION 1.0
    LANGUAGES CXX)

add_executable(3d-game-shaders-for-beginners
    src/main.cxx)

if(MSVC)
    set(PAND3D_INCLUDE_PATH "C:\\Panda3D-1.10.9-x64\\include")
    set(PAND3D_LIB_PATH "C:\\Panda3D-1.10.9-x64\\lib")

    set_target_properties(3d-game-shaders-for-beginners
        PROPERTIES
        RUNTIME_OUTPUT_DIRECTORY "${PROJECT_SOURCE_DIR}"
        RUNTIME_OUTPUT_DIRECTORY_DEBUG "${PROJECT_SOURCE_DIR}"
        RUNTIME_OUTPUT_DIRECTORY_RELEASE "${PROJECT_SOURCE_DIR}"
    )
endif()

target_include_directories(3d-game-shaders-for-beginners
    PRIVATE "${PAND3D_INCLUDE_PATH}")

find_library(P3FRAMEWORK_LIB libp3framework PATHS "${PAND3D_LIB_PATH}")
find_library(PANDA_LIB libpanda PATHS "${PAND3D_LIB_PATH}")
find_library(PANDAFX_LIB libpandafx PATHS "${PAND3D_LIB_PATH}")
find_library(PANDAEXPRESS_LIB libpandaexpress PATHS "${PAND3D_LIB_PATH}")
find_library(PANDAPHYSICS_LIB libpandaphysics PATHS "${PAND3D_LIB_PATH}")
find_library(P3DTOOLCONFIG_LIB libp3dtoolconfig PATHS "${PAND3D_LIB_PATH}")
find_library(P3DTOOL_LIB libp3dtool PATHS "${PAND3D_LIB_PATH}")

target_link_libraries(3d-game-shaders-for-beginners
    PRIVATE "${P3FRAMEWORK_LIB}"
    PRIVATE "${PANDA_LIB}"
    PRIVATE "${PANDAFX_LIB}"
    PRIVATE "${PANDAEXPRESS_LIB}"
    PRIVATE "${PANDAPHYSICS_LIB}"
    PRIVATE "${P3DTOOLCONFIG_LIB}"
    PRIVATE "${P3DTOOL_LIB}")
