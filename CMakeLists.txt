cmake_minimum_required(VERSION 3.14)

project(8-step-hack)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOMOC ON)

set(CMAKE_PREFIX_PATH ${CMAKE_PREFIX_PATH} "C:\\Qt\\5.15.0\\msvc2019_64\\")

find_package(Qt5 COMPONENTS Core Gui Widgets)

# Make sure all source files are present to avoid obscure compiler errors.
set(HACK_SOURCES
    "${CMAKE_SOURCE_DIR}/hack.cpp"
)
foreach(FILE ${HACK_SOURCES})
    if(NOT EXISTS "${FILE}")
        message(FATAL_ERROR "File ${FILE} does not exist.")
    endif()
endforeach()

# Add executable
add_executable(${PROJECT_NAME} ${HACK_SOURCES})
target_link_libraries(${PROJECT_NAME} Qt5::Core Qt5::Gui Qt5::Widgets)
