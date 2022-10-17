project(cmsis)

option(CMSIS_CORE_LIB           "Build CMSIS Core library"          OFF)
option(CMSIS_CORE_A_LIB         "Build CMSIS Core_A library"        OFF)    
option(CMSIS_DSP                "Build CMSIS DSP library"           OFF)    
option(CMSIS_NN                 "Build CMSIS NN library"            OFF)    
option(CMSIS_RTOS               "Build CMSIS RTOS library"          OFF)    
option(CMSIS_RTOS2              "Build CMSIS RTOS2 library"         OFF)   

set(MCU_FAMILY STM32F4xx)

set(CMSIS_DIRECTORIES
    ${CMAKE_CURRENT_LIST_DIR}/Include
    ${CMAKE_CURRENT_LIST_DIR}/Device/ST/${MCU_FAMILY}/Include
)

add_library(${PROJECT_NAME} STATIC)
add_library(cmsis::lib ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME}
    PUBLIC
        ${CMSIS_DIRECTORIES}
)

target_sources(${PROJECT_NAME}
    PUBLIC
        ${CMSIS_DIRECTORIES}
)

set_target_properties(${PROJECT_NAME} PROPERTIES LINKER_LANGUAGE C)

if(${CMSIS_CORE_LIB})
    add_subdirectory(Core)
endif()

if(${CMSIS_CORE_A_LIB})
    add_subdirectory(Core_A)
endif()

if(${CMSIS_DSP})
    add_subdirectory(DSP)
endif()

if(${CMSIS_NN})
    add_subdirectory(NN)
endif()

if(${CMSIS_RTOS})
    add_subdirectory(RTOS)
endif()

if(${CMSIS_RTOS2})
    add_subdirectory(RTOS2)
endif()
