project(middleware_usb_host)

set(MIDDLEWARE_USB_HOST_DIRECTORIES
    ${CMAKE_CURRENT_LIST_DIR}/Core/Inc
)

set(MIDDLEWARE_USB_HOST_SOURCES
    ${CMAKE_CURRENT_LIST_DIR}/Core/Src/usbh_conf_template.c
    ${CMAKE_CURRENT_LIST_DIR}/Core/Src/usbh_core.c
    ${CMAKE_CURRENT_LIST_DIR}/Core/Src/usbh_ctlreq.c
    ${CMAKE_CURRENT_LIST_DIR}/Core/Src/usbh_ioreq.c
    ${CMAKE_CURRENT_LIST_DIR}/Core/Src/usbh_pipes.c
)

add_library(${PROJECT_NAME} EXCLUDE_FROM_ALL ${MIDDLEWARE_USB_DEV_SOURCES})
add_library(middleware_usb_host::lib ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME}
    PUBLIC
        ${MIDDLEWARE_USB_HOST_DIRECTORIES}
)

target_sources(${PROJECT_NAME}
    PUBLIC
        ${MIDDLEWARE_USB_HOST_DIRECTORIES}
    PRIVATE
        ${MIDDLEWARE_USB_HOST_SOURCES}
)
