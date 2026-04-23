add_library(lmdb STATIC)
target_sources(
    lmdb
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/mdb.c
        ${CMAKE_CURRENT_SOURCE_DIR}/midl.c
)
target_include_directories(lmdb PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

include(GNUInstallDirs)
install(
    TARGETS lmdb
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
)
install(
    FILES lmdb.h
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)
configure_file(${CMAKE_SOURCE_DIR}/packaging/lmdb.pc.in lmdb.pc @ONLY)
install(
    FILES ${CMAKE_CURRENT_BINARY_DIR}/lmdb.pc
    DESTINATION ${CMAKE_INSTALL_LIBDIR}/pkgconfig
)
