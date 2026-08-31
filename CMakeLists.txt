# Defines a static library
# 'STATIC' means the compiled code from these files will be bundled into a .a archive
add_library(rpmsg_lite STATIC
    lib/common/llist.c
    lib/rpmsg_lite/porting/environment/rpmsg_env_freertos.c
    lib/rpmsg_lite/porting/platform/imx7d_m4/rpmsg_platform.c
    lib/rpmsg_lite/rpmsg_lite.c
    lib/rpmsg_lite/rpmsg_ns.c
    lib/rpmsg_lite/rpmsg_queue.c
    lib/virtio/virtqueue.c
)

# Specifies include directories
# 'PUBLIC' means these paths will be inherited by targets that link to 'rpmsg_lite'
target_include_directories(rpmsg_lite PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/lib/include
    ${CMAKE_CURRENT_SOURCE_DIR}/lib/include/platform
    ${CMAKE_CURRENT_SOURCE_DIR}/lib/include/platform/imx7d_m4
    ${CMAKE_SOURCE_DIR}/imx7d_com_m4_config
    ${CMAKE_SOURCE_DIR}/imx7d_com_m4
    ${CMAKE_SOURCE_DIR}/imx-hal/platform/devices
    ${CMAKE_SOURCE_DIR}/imx-hal/platform/devices/MCIMX7D/include
    ${CMAKE_SOURCE_DIR}/imx-hal/platform/CMSIS/Include
    ${CMAKE_SOURCE_DIR}/imx-hal/platform/devices/MCIMX7D/startup
    ${CMAKE_SOURCE_DIR}/imx-hal/platform/drivers/inc
)

# Links the 'freertos' library to 'rpmsg_lite'
# 'PUBLIC' means that any target linking to 'rpmsg_lite' will also automatically link to 'freertos'
target_link_libraries(rpmsg_lite PUBLIC freertos)
