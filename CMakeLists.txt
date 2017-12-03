cmake_minimum_required(VERSION 3.5)
project(ssd1306)

set(CMAKE_BUILD_TYPE Release)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -std=c++14")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall")

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/bin)

FILE (GLOB SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/lib/*.cxx")
FILE (GLOB HEADERS "${CMAKE_CURRENT_SOURCE_DIR}/lib/*.h")

include_directories(${PROJECT_SOURCE_DIR}/lib)

set(EXTRA_LIBS ${EXTRA_LIBS} HD44780Lcd)

add_library (${PROJECT_NAME} SHARED ${SOURCES})
set_target_properties (${PROJECT_NAME} PROPERTIES VERSION 1.0 SOVERSION 1)

add_executable(analog examples/analog.cxx examples/LinuxKeys.cxx)
target_link_libraries(analog ${PROJECT_NAME})

add_executable(clock examples/clock.cxx examples/LinuxKeys.cxx)
target_link_libraries(clock ${PROJECT_NAME})

add_executable(ipaddress examples/ipaddress.cxx examples/LinuxKeys.cxx)
target_link_libraries(ipaddress ${PROJECT_NAME})

add_executable(life examples/life.cxx examples/LinuxKeys.cxx)
target_link_libraries(life ${PROJECT_NAME})

add_executable(testbitmap examples/testbitmap.cxx examples/LinuxKeys.cxx)
target_link_libraries(testbitmap ${PROJECT_NAME})

add_executable(testoled examples/testoled.cxx examples/LinuxKeys.cxx)
target_link_libraries(testoled ${PROJECT_NAME})

