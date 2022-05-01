# CMakeLists files in this project can
# refer to the root source directory of the project as ${HELLO_SOURCE_DIR} and
# to the root binary directory of the project as ${HELLO_BINARY_DIR}.
cmake_minimum_required (VERSION 3.10.0)

IF (CONFIG STREQUAL YES)
    ADD_DEFINITIONS(-DHAVE_CONFIG_H)
ENDIF()

project (gst-template)

set(GST_DIR ${PROJECT_SOURCE_DIR}/../gstreamer)
message("GST dir : ${GST_DIR}")

set(HEADER_FILE gst.h)
# Add the support library
find_path(GST_INCLUDE_DIR 
          ${HEADER_FILE}
          HINTS ${GST_DIR}/gst)
if(NOT GST_INCLUDE_DIR)
    message(WARNING "Gst head file (${HEADER_FILE}) not found")
else()
    message(STATUS "Gst head file located at: ${GST_INCLUDE_DIR}")
    include_directories(${GST_INCLUDE_DIR}/..)
    include_directories(${GST_INCLUDE_DIR}/../build)
endif()   

set(GSTLIB ${GST_DIR}/build/gst/libgstreamer-1.0.so)
set(GOBJLIB gobject-2.0)

##glib
find_package(PkgConfig REQUIRED)
pkg_search_module(GLIB REQUIRED glib-2.0)
include_directories(${GLIB_INCLUDE_DIRS})
link_directories(${GLIB_LIBRARY_DIRS})
MESSAGE(STATUS "glib-2.0 include dirs:" ${GLIB_INCLUDE_DIRS})
MESSAGE(STATUS "glib-2.0 lib:" ${GLIB_LIBRARIES})

add_subdirectory (app)
add_subdirectory (plugin)