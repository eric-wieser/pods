cmake_minimum_required(VERSION 2.6.0)

# pull in the pods macros. See cmake/pods.cmake for documentation
set(POD_NAME ${pod_name})
include(cmake/pods.cmake)

# automatically build LCM types.  This also defines a number of CMake
# variables, see cmake/lcmtypes.cmake for details
include(cmake/lcmtypes.cmake)
lcmtypes_build()

include_directories(${LCMTYPES_INCLUDE_DIRS})

# build two LCM test programs
add_executable(send_message src/send_message.c)
target_link_libraries(send_message ${LCMTYPES_LIBS})
pods_use_pkg_config_packages(send_message lcm)

add_executable(listener src/listener.c)
target_link_libraries(listener ${LCMTYPES_LIBS})
pods_use_pkg_config_packages(listener lcm)

# make exeutables public
pods_install_executables(send_message listener)
