add_definitions(-DTRANSLATION_DOMAIN="pkupdates")

set(plasmapk_qmlplugins_SRCS
   qmlplugins.cpp
   pkupdates.cpp
   PkStrings.cpp
)

add_library(plasmapk_qmlplugins SHARED ${plasmapk_qmlplugins_SRCS})

target_link_libraries(plasmapk_qmlplugins
    Qt5::Core
    Qt5::Qml
    Qt5::DBus
    KF5::I18n
    KF5::CoreAddons
    KF5::Notifications
    KF5::IconThemes
    KF5::ConfigCore
    KF5::KDELibs4Support
    PK::packagekitqt5
)

install(TARGETS plasmapk_qmlplugins DESTINATION ${QML_INSTALL_DIR}/org/kde/plasma/PackageKit)
install(FILES qmldir DESTINATION ${QML_INSTALL_DIR}/org/kde/plasma/PackageKit)

# test binary
set(plasmapk_console_SRCS
   pkupdates.cpp
   PkStrings.cpp
   main.cpp
)

add_executable(plasmapk-console ${plasmapk_console_SRCS})

target_link_libraries(plasmapk-console
    Qt5::Core
    KF5::I18n
    KF5::CoreAddons
    KF5::ConfigCore
    KF5::KDELibs4Support
    KF5::Notifications
    KF5::IconThemes
    PK::packagekitqt5
)
