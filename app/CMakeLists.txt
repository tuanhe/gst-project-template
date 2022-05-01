AUX_SOURCE_DIRECTORY(./src  gst_app_source_files)
list(APPEND gst_app_sources ${gst_app_source_files})

add_executable(gst-app ${gst_app_sources})

target_link_libraries(gst-app PRIVATE ${GLIB_LIBRARIES} ${GSTLIB} ${GOBJLIB})