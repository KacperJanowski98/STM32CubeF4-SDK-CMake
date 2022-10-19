cmake_minimum_required(VERSION 3.20)

option(MIDDLEWARES_BUILD       "Build Middlewares for stm32f4"       OFF)

project(stm32-sdk-cmake)

add_subdirectory(Drivers)

if(MIDDLEWARES_BUILD)
    add_subdirectory(Middlewares)
endif()
