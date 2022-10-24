project(cmsis_core)

set(CMSIS_CORE_DIRECTORIES
    ${CMAKE_CURRENT_LIST_DIR}/Include
)

add_library(${PROJECT_NAME} EXCLUDE_FROM_ALL)
add_library(cmsis_core::lib ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME}
    PUBLIC
        ${CMSIS_CORE_DIRECTORIES}
)

target_sources(${PROJECT_NAME}
    PUBLIC
        ${CMSIS_CORE_DIRECTORIES}
)

set_target_properties(${PROJECT_NAME} PROPERTIES LINKER_LANGUAGE C)
