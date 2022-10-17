project(cmsis_rtos2)

set(CMSIS_RTOS2_DIRECTORIES
    ${CMAKE_CURRENT_LIST_DIR}/Include
)

set(CMSIS_RTOS2_SOURCES
    ${CMAKE_CURRENT_LIST_DIR}/Source/os_systick.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/os_tick_gtim.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/os_tick_ptim.c
)

add_library(${PROJECT_NAME} STATIC ${CMSIS_RTOS2_SOURCES})
add_library(cmsis_rtos2::lib ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME}
    PUBLIC
        ${CMSIS_RTOS2_DIRECTORIES}
)

target_sources(${PROJECT_NAME}
    PUBLIC
        ${CMSIS_RTOS2_DIRECTORIES}
    PRIVATE
        ${CMSIS_RTOS2_SOURCES}
)
