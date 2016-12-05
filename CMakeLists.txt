project(QSimpleUpdater) 
cmake_minimum_required(VERSION 3.6)

find_package(Qt5Widgets)
find_package(Qt5Network)

set(CMAKE_AUTOMOC ON)
add_definitions(${QT_DEFINITIONS}) 

include_directories(${Qt5Widgets_INCLUDE_DIRS} 
                    ${Qt5Network_INCLUDE_DIRS}
					${CMAKE_CURRENT_SOURCE_DIR}/include
					${CMAKE_CURRENT_SOURCE_DIR}/src
					${CMAKE_CURRENT_BINARY_DIR})

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

add_library(QSimpleUpdater OBJECT ${SOURCE} ${HEADERS} ${UI_HEADERS} ${UI_RESOURCES})
set(QSimpleUpdater_INCLUDE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/include" "${CMAKE_CURRENT_SOURCE_DIR}/src" PARENT_SCOPE)