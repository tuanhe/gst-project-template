# Add executable called "helloDemo" that is built from the source files
# "demo.cxx" and "demo_b.cxx". The extensions are automatically found.
AUX_SOURCE_DIRECTORY(src  gst_plugin_source_files)
list(APPEND gst_plugin_sources ${gst_plugin_source_files})

message("Files are ${gst_plugin_sources}")
message("Project source dir ${PROJECT_SOURCE_DIR}")

list(REMOVE_ITEM SOURCE_FILES ${REMOVE_SOURCES})

add_library(gst-plugin SHARED ${gst_plugin_sources})

# Link the executable to the Hello library. Since the Hello library has
# public include directories we will use those link directories when building
# helloDemo
#target_link_libraries (helloDemo LINK_PUBLIC Hello)
target_include_directories(gst-plugin PRIVATE ${PROJECT_SOURCE_DIR}/src)