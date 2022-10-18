option(MIDDLEWARES_BUILD       "Build Middlewares for stm32f4"       OFF)

if(MIDDLEWARES_BUILD)
    add_subdirectory(ST)
    add_subdirectory(Third_Party)
endif()
