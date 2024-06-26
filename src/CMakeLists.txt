#  Set minimum required version of CMake
cmake_minimum_required(VERSION 3.12)
set(PICO_BOARD pico_w)

# Include build functions fom Pico SDK
include($ENV{PICO_SDK_PATH}/external/pico_sdk_import.cmake)

# Set name of project (as PROJECT_NAME) and C/C++ standards
project(PicoFurby C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Creates a pico-sdk subdirectory in our project for the libraries
pico_sdk_init()

# Tell CMmake where to find the executable source file
add_executable(${PROJECT_NAME}
pico-furby.c
)

# Create map/bin/hex/uf2 files
pico_add_extra_outputs(${PROJECT_NAME})

# Linke to pico_stdlib (gpio, time, etc, functions)
target_link_libraries(${PROJECT_NAME}
    pico_stdlib
    pico_cyw43_arch_none
)