set(kcm_fontinst_PART_SRCS ${libkfontinstview_SRCS} ${libkfontinstjobrunner_SRCS} ${libkfontinstdbusiface_SRCS}
    DuplicatesDialog.cpp FontList.cpp GroupList.cpp KCmFontInst.cpp PrintDialog.cpp
    FontFilter.cpp FontFilterProxyStyle.cpp FcQuery.cpp PreviewList.cpp)
# qt5_add_dbus_interface(kcm_fontinst_PART_SRCS ../dbus/org.kde.fontinst.xml FontinstIface)

add_library(kcm_fontinst MODULE ${kcm_fontinst_PART_SRCS})

target_link_libraries(kcm_fontinst
    KF5::Archive
    KF5::KCMUtils
    KF5::IconThemes
    KF5::KIOCore
    KF5::KIOWidgets
    KF5::XmlGui
    KF5::NewStuff
    kfontinstui
    kfontinst
    ${X11_LIBRARIES}
)

install(TARGETS kcm_fontinst  DESTINATION ${PLUGIN_INSTALL_DIR} )
install( FILES fontinst.desktop  DESTINATION  ${SERVICES_INSTALL_DIR} )
install( FILES kfontinst.knsrc DESTINATION  ${CONFIG_INSTALL_DIR} )

ecm_install_icons( ICONS
                   16-actions-addfont.png
                   16-actions-disablefont.png
                   16-actions-enablefont.png
                   16-actions-fontstatus.png
                   22-actions-addfont.png
                   22-actions-disablefont.png
                   22-actions-enablefont.png
                   22-actions-fontstatus.png
                   16-actions-addfont.png
                   DESTINATION
                   ${DATA_INSTALL_DIR}/kfontinst/icons THEME hicolor)
