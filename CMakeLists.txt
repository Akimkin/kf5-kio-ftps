cmake_minimum_required(VERSION 3.3)
project(kf5-kio-ftps)

find_package(ECM 0.0.11 REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${ECM_KDE_MODULE_DIR})

include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings)
include(FeatureSummary)

find_package(Qt5 REQUIRED COMPONENTS Network Widgets)
find_package(KF5 REQUIRED COMPONENTS KIO CoreAddons WidgetsAddons)

feature_summary(WHAT ALL FATAL_ON_MISSING_REQUIRED_PACKAGES)

add_library(kio_ftps MODULE ftp.cpp)
target_link_libraries(kio_ftps Qt5::Core Qt5::Network Qt5::Widgets KF5::KIOCore KF5::WidgetsAddons)

install(TARGETS kio_ftps DESTINATION ${PLUGIN_INSTALL_DIR})
install(FILES ftps.protocol DESTINATION ${SERVICES_INSTALL_DIR})
