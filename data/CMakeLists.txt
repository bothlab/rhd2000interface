 
# .desktop file
install(FILES rhd2000interface.desktop DESTINATION "${CMAKE_INSTALL_DATADIR}/applications")

# icon
install(FILES rhd2000interface.svg DESTINATION "${CMAKE_INSTALL_DATADIR}/icons/hicolor/scalable/apps/")

# Rhythm bitfile
install(FILES main.bit DESTINATION "${CMAKE_INSTALL_DATADIR}/intan/rhd2000interface/")
