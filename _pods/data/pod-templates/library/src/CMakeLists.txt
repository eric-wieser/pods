# Create a shared library libhello.so with a single source file
add_library(hello SHARED
    hello.c)

# set the library API version.  Increment this every time the public API
# changes.
set_target_properties(hello PROPERTIES SOVERSION 1)

# make the header public
# install it to include/hello
pods_install_headers(hello.h DESTINATION hello)

# make the library public
pods_install_libraries(hello)

# create a pkg-config file for the library, to make it for other software to
# use it.
pods_install_pkg_config_file(hello
    CFLAGS
    LIBS -lhello
    VERSION 0.0.1)
