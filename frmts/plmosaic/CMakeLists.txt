add_gdal_driver(TARGET gdal_PLMOSAIC SOURCES plmosaicdataset.cpp PLUGIN_CAPABLE_IF "NOT GDAL_USE_LIBJSONC_INTERNAL"
                                             NO_DEPS)
gdal_standard_includes(gdal_PLMOSAIC)
target_include_directories(gdal_PLMOSAIC PRIVATE ${GDAL_VECTOR_FORMAT_SOURCE_DIR}/geojson)
if (GDAL_USE_LIBJSONC_INTERNAL)
  target_include_directories(gdal_PLMOSAIC PRIVATE $<TARGET_PROPERTY:libjson,SOURCE_DIR>)
else ()
  gdal_target_link_libraries(TARGET gdal_PLMOSAIC LIBRARIES JSONC::JSONC)
endif ()
