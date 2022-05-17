cmake_minimum_required ( VERSION 3.1.0 )

project ( RTWeekend
  VERSION 3.0.0
  LANGUAGES CXX
)

set ( CMAKE_CXX_STANDARD 17 )

find_package(OpenCV REQUIRED)

set ( SOURCE_ONE_WEEKEND
  src/camera.h
  src/ray.h
  src/vec3.h
  src/hitable.h
  src/hitable_list.h
  src/material.h
  src/sphere.h
  src/random.h
  src/main.cpp
)

add_executable(inOneWeekend      ${SOURCE_ONE_WEEKEND})
target_link_libraries(inOneWeekend "${OpenCV_LIBS}")
include_directories(src)
