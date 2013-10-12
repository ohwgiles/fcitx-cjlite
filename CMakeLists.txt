cmake_minimum_required(VERSION 2.6)

project(fcitx-cangjie NONE)

find_package(Fcitx 4.2.5 REQUIRED)
find_package(Gettext REQUIRED)
find_program(TXT2MB txt2mb REQUIRED)

configure_file(cmake_uninstall.cmake.in cmake_uninstall.cmake IMMEDIATE @ONLY)

add_custom_target(uninstall COMMAND ${CMAKE_COMMAND} -P ${CMAKE_CURRENT_BINARY_DIR}/cmake_uninstall.cmake)

add_subdirectory(po)

intltool_merge_translation(${CMAKE_CURRENT_SOURCE_DIR}/fcitx-cangjie.conf.in ${CMAKE_CURRENT_BINARY_DIR}/fcitx-cangjie.conf)

add_custom_command(OUTPUT fcitx-cangjie.mb
		DEPENDS fcitx-cangjie.txt
		COMMAND ${TXT2MB} ARGS ${CMAKE_CURRENT_SOURCE_DIR}/fcitx-cangjie.txt ${CMAKE_CURRENT_BINARY_DIR}/fcitx-cangjie.mb)
add_custom_target(table_data ALL DEPENDS fcitx-cangjie.conf fcitx-cangjie.mb)

install(FILES fcitx-cangjie.conf DESTINATION ${FCITX4_PREFIX}/share/fcitx/table)
install(FILES fcitx-cangjie.mb DESTINATION ${FCITX4_PREFIX}/share/fcitx/table)
