project(kio-ftps)

find_package(KDE4 REQUIRED)

include_directories( ${KDE4_INCLUDES} )

set(mySources ftp.cpp)

kde4_add_plugin( kio_ftps ${mySources} )

target_link_libraries(kio_ftps ${KDE4_KDECORE_LIBS} kio )

install(TARGETS kio_ftps  DESTINATION ${PLUGIN_INSTALL_DIR} )
install( FILES ftps.protocol  DESTINATION  ${SERVICES_INSTALL_DIR} )
