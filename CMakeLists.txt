cmake_minimum_required(VERSION 3.7)

project(qthttp VERSION 2.0 LANGUAGES CXX)

include(CPack)

add_subdirectory(src)

install(EXPORT ${CMAKE_PROJECT_NAME}
    NAMESPACE ${CMAKE_PROJECT_NAME}::
    DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/${CMAKE_PROJECT_NAME}
    FILE ${CMAKE_PROJECT_NAME}-config.cmake)
