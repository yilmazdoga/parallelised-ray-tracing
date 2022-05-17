cmake_minimum_required ( VERSION 3.1.0 )

project ( RTWeekend
  VERSION 3.0.0
  LANGUAGES CXX
)

set ( CMAKE_CXX_STANDARD 17 )

set(CMAKE_C_COMPILER "/usr/local/Cellar/llvm/13.0.1_1/bin/clang")
set(CMAKE_CXX_COMPILER "/usr/local/Cellar/llvm/13.0.1_1/bin/clang++")
set(OPENMP_LIBRARIES "/usr/local/Cellar/libomp/14.0.0/lib")
set(OPENMP_INCLUDES "/usr/local/Cellar/libomp/14.0.0/include")

OPTION (USE_OpenMP "Use OpenMP to enamble <omp.h>" ON)

set(OpenMP_C "${CMAKE_C_COMPILER}")
set(OpenMP_C_FLAGS "-fopenmp=libomp -Wno-unused-command-line-argument")
set(OpenMP_C_LIB_NAMES "libomp" "libgomp" "libiomp5")
set(OpenMP_libomp_LIBRARY ${OpenMP_C_LIB_NAMES})
set(OpenMP_libgomp_LIBRARY ${OpenMP_C_LIB_NAMES})
set(OpenMP_libiomp5_LIBRARY ${OpenMP_C_LIB_NAMES})

set(OpenMP_CXX "${CMAKE_CXX_COMPILER}")
set(OpenMP_CXX_FLAGS "-fopenmp=libomp -Wno-unused-command-line-argument")
set(OpenMP_CXX_LIB_NAMES "libomp" "libgomp" "libiomp5")
set(OpenMP_libomp_LIBRARY ${OpenMP_CXX_LIB_NAMES})
set(OpenMP_libgomp_LIBRARY ${OpenMP_CXX_LIB_NAMES})
set(OpenMP_libiomp5_LIBRARY ${OpenMP_CXX_LIB_NAMES})

find_package(OpenMP REQUIRED)
find_package(OpenCV REQUIRED)

include_directories("${OPENMP_INCLUDES}")
link_directories("${OPENMP_LIBRARIES}")
set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")


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
