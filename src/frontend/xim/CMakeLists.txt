add_fcitx5_addon(xim xim.cpp)
target_link_libraries(xim Fcitx5::Core XCBImdkit::XCBImdkit XCB::XCB XCB::AUX XCB::EWMH XKBCommon::XKBCommon Fcitx5::Module::XCB)
target_compile_definitions(xim PRIVATE -DFCITX_XCB_EWMH)
install(TARGETS xim DESTINATION "${FCITX_INSTALL_ADDONDIR}")
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/xim.conf" DESTINATION "${FCITX_INSTALL_PKGDATADIR}/addon"
        COMPONENT config)

configure_file(xim.conf.in.in xim.conf.in @ONLY)
fcitx5_translate_desktop_file(${CMAKE_CURRENT_BINARY_DIR}/xim.conf.in xim.conf)
