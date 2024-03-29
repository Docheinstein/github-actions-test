
# zlib
set(ZLIB_BUILD_EXAMPLES OFF)
set(SKIP_INSTALL_ALL ON)
add_subdirectory(zlib)

# Explicitly set ZLIB::ZLIB as an alias for zlibstatic so that libpng will use this.
add_library(ZLIB::ZLIB ALIAS zlibstatic)

# libpng
# Copy prebuilt pnglibconf.h into libpng source directory.
# We must to do so even if it is available system wise because we want to
# statically link the zlib library we have built; otherwise the libpng might
# complain because of zlib's version mismatch.
configure_file(${CMAKE_CURRENT_SOURCE_DIR}/libpng/scripts/pnglibconf.h.prebuilt
           ${CMAKE_CURRENT_SOURCE_DIR}/libpng/pnglibconf.h)

set(PNG_SHARED OFF CACHE BOOL "Build libpng as a shared library")
set(PNG_STATIC ON CACHE BOOL "Build libpng as a static library")
set(PNG_TESTS OFF CACHE BOOL "Build the libpng tests")
set(PNG_TOOLS OFF CACHE BOOL "Build the libpng tools")
# add_subdirectory(libpng)