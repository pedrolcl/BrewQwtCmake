cmake_minimum_required(VERSION 3.15)
project(barchart)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)
find_package(Qt5 COMPONENTS Widgets REQUIRED)

set(CMAKE_FIND_FRAMEWORK ONLY)
find_library(QWT
    NAMES qwt
    HINTS /usr/local/opt/qwt/lib/
    REQUIRED)
if (QWT)
    message("QWT found: ${QWT}")
    include_directories(${QWT}/Headers)
    link_libraries(${QWT})
endif()

set(SOURCES barchart.cpp main.cpp barchart.h)

add_executable(barchart ${SOURCES})

target_link_libraries(barchart Qt5::Widgets)
