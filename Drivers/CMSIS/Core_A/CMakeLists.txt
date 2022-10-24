project(cmsis_core_a)

set(CMSIS_CORE_A_DIRECTORIES
    ${CMAKE_CURRENT_LIST_DIR}/Include
)

set(CMSIS_CORE_A_SOURCES
    ${CMAKE_CURRENT_LIST_DIR}/Source/irq_ctrl_gic.c
)

add_library(${PROJECT_NAME} EXCLUDE_FROM_ALL ${CMSIS_CORE_A_SOURCES})
add_library(cmsis_core_a::lib ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME}
    PUBLIC
        ${CMSIS_CORE_DIRECTORIES}
)

target_sources(${PROJECT_NAME}
    PUBLIC
        ${CMSIS_CORE_DIRECTORIES}
    PRIVATE
        ${CMSIS_CORE_A_SOURCES}
)

set_target_properties(${PROJECT_NAME} PROPERTIES LINKER_LANGUAGE C)
