project(QSimpleUpdater) 
cmake_minimum_required(VERSION 3.6)

find_package(Qt5 COMPONENTS Widgets Network)

set(CMAKE_AUTOMOC ON)
cmake_policy(SET CMP0071 OLD)

qt5_wrap_ui(UI_HEADERS 
            src/Downloader.ui)

qt5_add_resources(UI_RESOURCES 
                 etc/resources/qsimpleupdater.qrc)

set(SOURCE
    src/Updater.cpp 
    src/Downloader.cpp 
    src/QSimpleUpdater.cpp
)

set(HEADERS
    include/QSimpleUpdater.h
    src/Updater.h
    src/Downloader.h
)

add_library(QSimpleUpdater STATIC ${SOURCE} ${HEADERS} ${UI_HEADERS} ${UI_RESOURCES})
target_link_libraries(QSimpleUpdater Qt5::Widgets Qt5::Network)
target_include_directories(QSimpleUpdater PUBLIC  ${CMAKE_CURRENT_SOURCE_DIR}/include 
                                                  ${CMAKE_CURRENT_SOURCE_DIR}/src
                                          PRIVATE ${CMAKE_CURRENT_BINARY_DIR})
