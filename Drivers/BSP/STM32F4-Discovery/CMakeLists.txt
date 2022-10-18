project(stm32f4_discover_bsp)

option(STM32F4_DISC_BUILD                       "Build BSP for stm32f4 discovery"       ON)
option(STM32F4_DISC_AUDIO_BUILD                 "Build BSP for stm32f4 discovery"       OFF)
option(STM32F4_DISC_ACCELEROMETER_BUILD         "Build BSP for stm32f4 discovery"       OFF)

if(STM32F4_DISC_BUILD)
    add_library(${PROJECT_NAME} STATIC ${CMAKE_CURRENT_LIST_DIR}/stm32f4_discovery.c)

    target_include_directories(${PROJECT_NAME}
        PUBLIC
            ${CMAKE_CURRENT_LIST_DIR}/stm32f4_discovery.h
    )

    target_sources(${PROJECT_NAME}
        PUBLIC
            ${CMAKE_CURRENT_LIST_DIR}/stm32f4_discovery.h
        PRIVATE
            ${CMAKE_CURRENT_LIST_DIR}/stm32f4_discovery.c
    )
endif()

if(STM32F4_DISC_AUDIO_BUILD)
    add_library(${PROJECT_NAME} STATIC ${CMAKE_CURRENT_LIST_DIR}/stm32f4_discovery_audio.c)

    target_include_directories(${PROJECT_NAME}
        PUBLIC
            ${CMAKE_CURRENT_LIST_DIR}/stm32f4_discovery_audio.h
    )

    target_sources(${PROJECT_NAME}
        PUBLIC
            ${CMAKE_CURRENT_LIST_DIR}/stm32f4_discovery_audio.h
        PRIVATE
            ${CMAKE_CURRENT_LIST_DIR}/stm32f4_discovery_audio.c
    )
endif()

if(STM32F4_DISC_ACCELEROMETER_BUILD)
    add_library(${PROJECT_NAME} STATIC ${CMAKE_CURRENT_LIST_DIR}/stm32f4_discovery_accelerometer.c)

    target_include_directories(${PROJECT_NAME}
        PUBLIC
            ${CMAKE_CURRENT_LIST_DIR}/stm32f4_discovery_accelerometer.h
    )

    target_sources(${PROJECT_NAME}
        PUBLIC
            ${CMAKE_CURRENT_LIST_DIR}/stm32f4_discovery_accelerometer.h
        PRIVATE
            ${CMAKE_CURRENT_LIST_DIR}/stm32f4_discovery_accelerometer.c
    )
endif()

add_library(stm32f4_discover_bsp::lib ALIAS ${PROJECT_NAME})
