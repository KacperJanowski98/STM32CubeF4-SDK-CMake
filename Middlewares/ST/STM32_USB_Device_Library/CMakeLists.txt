project(middleware_usb_dev)

set(MIDDLEWARE_USB_DEV_DIRECTORIES
    ${CMAKE_CURRENT_LIST_DIR}/Core/Inc
)

set(MIDDLEWARE_USB_DEV_SOURCES
    ${CMAKE_CURRENT_LIST_DIR}/Core/Src/usbd_conf_template.c
    ${CMAKE_CURRENT_LIST_DIR}/Core/Src/usbd_core.c
    ${CMAKE_CURRENT_LIST_DIR}/Core/Src/usbd_ctlreq.c
    ${CMAKE_CURRENT_LIST_DIR}/Core/Src/usbd_desc_template.c
    ${CMAKE_CURRENT_LIST_DIR}/Core/Src/usbd_ioreq.c
)

add_library(${PROJECT_NAME} EXCLUDE_FROM_ALL ${MIDDLEWARE_USB_DEV_SOURCES})
add_library(middleware_usb_dev::lib ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME}
    PUBLIC
        ${MIDDLEWARE_USB_DEV_DIRECTORIES}
)

target_sources(${PROJECT_NAME}
    PUBLIC
        ${MIDDLEWARE_USB_DEV_DIRECTORIES}
    PRIVATE
        ${MIDDLEWARE_USB_DEV_SOURCES}
)
