cmake_minimum_required(VERSION 2.6.0)

# pull in the pods macros. See cmake/pods.cmake for documentation
set(POD_NAME ${pod_name})
include(cmake/pods.cmake)

# require python
find_package(PythonInterp REQUIRED)

# 
pods_install_python_packages(${CMAKE_CURRENT_SOURCE_DIR}/python)

pods_install_python_script(hello-python hello.main)
