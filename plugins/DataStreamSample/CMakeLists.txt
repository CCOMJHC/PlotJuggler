
include_directories( ./ ../  ../../include  ../../common)

add_definitions(${QT_DEFINITIONS})
add_definitions(-DQT_PLUGIN)

SET( SRC
    datastream_sample.cpp
    ../../include/PlotJuggler/datastreamer_base.h )

add_library(DataStreamSample SHARED ${SRC} ${UI_SRC}  )
target_link_libraries(DataStreamSample  ${Qt5Widgets_LIBRARIES} ${Qt5Xml_LIBRARIES})

if(COMPILING_WITH_CATKIN)
    install(TARGETS DataStreamSample
        ARCHIVE DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
        LIBRARY DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
        RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION} )
elseif(COMPILING_WITH_AMENT)
    install(TARGETS DataStreamSample
            DESTINATION  lib/${PROJECT_NAME} )
else()
    install(TARGETS DataStreamSample DESTINATION bin  )
endif()
