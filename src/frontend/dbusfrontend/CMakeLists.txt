add_fcitx5_addon(dbusfrontend dbusfrontend.cpp)
target_link_libraries(dbusfrontend Fcitx5::Core Fcitx5::Module::DBus)
install(TARGETS dbusfrontend DESTINATION "${FCITX_INSTALL_ADDONDIR}")
configure_file(dbusfrontend.conf.in.in dbusfrontend.conf.in @ONLY)
fcitx5_translate_desktop_file(${CMAKE_CURRENT_BINARY_DIR}/dbusfrontend.conf.in dbusfrontend.conf)
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/dbusfrontend.conf" DESTINATION "${FCITX_INSTALL_PKGDATADIR}/addon"
        COMPONENT config)
