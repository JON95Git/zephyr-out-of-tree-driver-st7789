
list(APPEND ZEPHYR_EXTRA_MODULES
${CMAKE_CURRENT_SOURCE_DIR}/drivers
)

cmake_minimum_required(VERSION 3.20.0)

set(BOARD nrf52840_mdk)

find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(lvgl_nrf52840_mdk_sample)

FILE(GLOB app_sources 
    src/*.c
    )

target_sources(app PRIVATE ${app_sources})
