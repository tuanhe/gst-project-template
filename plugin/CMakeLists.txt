AUX_SOURCE_DIRECTORY(.  gst_plugin_source_files)
list(APPEND gst_plugin_sources ${gst_plugin_source_files})

message("Files are ${gst_plugin_sources}")
message("Project source dir ${PROJECT_SOURCE_DIR}")

#list(REMOVE_ITEM SOURCE_FILES ${REMOVE_SOURCES})

add_library(gst-plugin SHARED ${gst_plugin_sources})

#target_include_directories(gst-plugin PRIVATE ${PROJECT_SOURCE_DIR})
target_include_directories(gst-plugin PRIVATE .)
target_link_libraries(gst-plugin PRIVATE ${GSTLIB} ${GSTBASELIB})