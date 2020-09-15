
set(DIGIAPIX_ROOT "${CMAKE_CURRENT_LIST_DIR}")
set(DIGIAPIX_SRC "${DIGIAPIX_ROOT}/src")
set(DIGIAPIX_INCLUDE_PRIVATE "${DIGIAPIX_SRC}/include/private")
set(DIGIAPIX_INCLUDE "${DIGIAPIX_SRC}/include/public")
project(digiapix VERSION 1.1.0)

add_library(digiapix SHARED 
    ${DIGIAPIX_SRC}/adc.c
    ${DIGIAPIX_SRC}/can.c
    ${DIGIAPIX_SRC}/can_netlink.c
    ${DIGIAPIX_SRC}/common.c
    ${DIGIAPIX_SRC}/gpio.c
    ${DIGIAPIX_SRC}/i2c.c
    ${DIGIAPIX_SRC}/pwm.c
    ${DIGIAPIX_SRC}/pwr_management.c
    ${DIGIAPIX_SRC}/spi.c
    ${DIGIAPIX_SRC}/watchdog.c
)
target_include_directories(digiapix PUBLIC ${DIGIAPIX_INCLUDE} ${DIGIAPIX_INCLUDE_PRIVATE})
#target_include_directories(digiapix PRIVATE ${DIGIAPIX_INCLUDE_PRIVATE})

target_link_libraries(digiapix soc socketcan)
set_property(TARGET digiapix PROPERTY POSITION_INDEPENDENT_CODE ON)
set_target_properties(digiapix PROPERTIES VERSION ${PROJECT_VERSION})
