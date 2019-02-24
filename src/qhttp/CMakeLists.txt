set(target_name qhttp)

include(GNUInstallDirs)

find_package(Qt5 COMPONENTS Core Network REQUIRED)

set(CMAKE_AUTOMOC ON)

file(GLOB src *.cpp *.h)
file(GLOB public_headers qhttp.h)

add_library(${target_name} STATIC ${src})

target_include_directories(${target_name}
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}>
        $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>)

target_link_libraries(${target_name} PRIVATE
        Qt5::Core
        Qt5::Network)

set_target_properties(${target_name} PROPERTIES
    PUBLIC_HEADER "${public_headers}")

install(TARGETS ${target_name}
    EXPORT ${CMAKE_PROJECT_NAME}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
