option(STM32F4_DISC_BSP_BUILD       "Build BSP for stm32f4 discovery"       OFF)

add_subdirectory(CMSIS)
add_subdirectory(STM32F4xx_HAL_Driver)

if(STM32F4_DISC_BSP_BUILD)
    add_subdirectory(BSP)
endif()
