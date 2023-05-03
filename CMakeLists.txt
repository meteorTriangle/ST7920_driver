cmake_minimum_required(VERSION 3.13)

include(pico_sdk_import.cmake)
set(PICO_SDK_PATH "C:/rp2040/pico-sdk")
set(PICO_BOARD pico CACHE STRING "Board type")

project(ST7920_driver C CXX ASM)
add_library(ST7920_driver SHARED src/ST7920_driver.cpp)



target_include_directories(ST7920_driver PRIVATE
    ${PICO_SDK_PATH}
    externals/
)

pico_sdk_init()

target_include_directories(ST7920_driver PUBLIC
    ./include
)

target_link_libraries(ST7920_driver
        pico_stdlib
        LCD_parallel_driver
        hardware_gpio
        hardware_timer
        hardware_clocks)

##add_subdirectory(example/test_ST7920_init)