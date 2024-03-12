cmake_minimum_required(VERSION 2.8)
project(orb_cv)

set(CMAKE_BUILD_TYPE Release)
add_definitions("-DENABLE_SSE")
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "-std=c++14 -O2 ${SSE_FLAGS} -msse4")
list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)

find_package(OpenCV REQUIRED)
find_package(G2O REQUIRED)
find_package(Sophus REQUIRED)

include_directories(
        ${OpenCV_INCLUDE_DIRS}
        ${G2O_INCLUDE_DIRS}
        ${Sophus_INCLUDE_DIRS}
        "/usr/include/eigen3/"
)

add_executable(orb_dataset orb_dataset.cpp)
target_link_libraries(orb_dataset ${OpenCV_LIBS})
