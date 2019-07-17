# CMakeLists for the Intan RHD2000 Interface

if(WIN32)
  set(GUI_TYPE WIN32)
elseif(APPLE)
  set(GUI_TYPE MACOSX_BUNDLE)
endif()

set(RHD2000INTF_SRC
    main.cpp
    okFrontPanelDLL.h
    okFrontPanelDLL.cpp
    rhd2000evalboard.h
    rhd2000evalboard.cpp
    rhd2000registers.h
    rhd2000registers.cpp
    rhd2000datablock.h
    rhd2000datablock.cpp
    waveplot.h
    waveplot.cpp
    mainwindow.h
    mainwindow.cpp
    signalprocessor.h
    signalprocessor.cpp
    bandwidthdialog.h
    bandwidthdialog.cpp
    renamechanneldialog.h
    renamechanneldialog.cpp
    signalchannel.h
    signalchannel.cpp
    signalgroup.h
    signalgroup.cpp
    signalsources.h
    signalsources.cpp
    spikescopedialog.h
    spikescopedialog.cpp
    spikeplot.h
    spikeplot.cpp
    keyboardshortcutdialog.h
    keyboardshortcutdialog.cpp
    randomnumber.h
    randomnumber.cpp
    impedancefreqdialog.h
    impedancefreqdialog.cpp
    globalconstants.h
    triggerrecorddialog.h
    triggerrecorddialog.cpp
    setsaveformatdialog.h
    setsaveformatdialog.cpp
    helpdialoghighpassfilter.h
    helpdialoghighpassfilter.cpp
    helpdialognotchfilter.h
    helpdialognotchfilter.cpp
    helpdialogdacs.h
    helpdialogdacs.cpp
    helpdialogcomparators.h
    helpdialogcomparators.cpp
    helpdialogchipfilters.h
    helpdialogchipfilters.cpp
    auxdigoutconfigdialog.h
    auxdigoutconfigdialog.cpp
    cabledelaydialog.h
    cabledelaydialog.cpp
    helpdialogfastsettle.h
    helpdialogfastsettle.cpp
)

qt5_add_resources(RHD2000INTF_RES_SRC RHD2000interface.qrc)

add_executable(rhd2000interface
    ${GUI_TYPE}
    ${RHD2000INTF_SRC}
    ${RHD2000INTF_RES_SRC}
)

target_link_libraries(rhd2000interface
    ${CMAKE_DL_LIBS}
    Qt5::Widgets
    Qt5::Multimedia
)

install(TARGETS rhd2000interface DESTINATION ${CMAKE_INSTALL_BINDIR})

# Windows stuff
if ("${CMAKE_SYSTEM_NAME}" STREQUAL "Windows")
   add_definitions("-D_UNICODE" "-DUNICODE")
   set_target_properties(rhd2000interface PROPERTIES LINK_FLAGS_DEBUG "/SUBSYSTEM:CONSOLE")
   set_target_properties(rhd2000interface PROPERTIES COMPILE_DEFINITIONS_DEBUG "_CONSOLE")
   set_target_properties(rhd2000interface PROPERTIES LINK_FLAGS_RELWITHDEBINFO "/SUBSYSTEM:windows")
   set_target_properties(rhd2000interface PROPERTIES LINK_FLAGS_RELEASE "/SUBSYSTEM:windows")
   set_target_properties(rhd2000interface PROPERTIES LINK_FLAGS_MINSIZEREL "/SUBSYSTEM:windows")
endif()
