project(cmsis_rtos)

set(CMSIS_RTOS_DIRECTORIES
    ${CMAKE_CURRENT_LIST_DIR}/Template
)

add_library(${PROJECT_NAME} EXCLUDE_FROM_ALL)
add_library(cmsis_rtos::lib ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME}
    PUBLIC
        ${CMSIS_RTOS_DIRECTORIES}
)

target_sources(${PROJECT_NAME}
    PUBLIC
        ${CMSIS_RTOS_DIRECTORIES}
)

set_target_properties(${PROJECT_NAME} PROPERTIES LINKER_LANGUAGE C)
