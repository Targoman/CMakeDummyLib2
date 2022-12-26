cmake_minimum_required(VERSION 3.16)
project(CMakeBuildSampleLib VERSION 0.0.1)

include(./Targoman.cmake)
setup_bs_paths()

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt5 COMPONENTS Core Test REQUIRED)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

add_subdirectory(3rdParty)

add_library(DummyLib2
    SHARED
    libsrc/libDummyLib2/clsSample.cpp
)
set_target_properties(DummyLib2
    PROPERTIES
    PUBLIC_HEADER
    libsrc/libDummyLib2/clsSample.h
)
target_link_libraries(DummyLib2 Qt5::Core)
target_link_libraries(DummyLib2 DummyLib1)

export_public_headers(DummyLib2)