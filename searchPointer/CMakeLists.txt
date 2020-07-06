cmake_minimum_required(VERSION 3.16)
project(searchPointer)

find_package(Boost REQUIRED COMPONENTS system)
find_package(Threads REQUIRED)
find_package(ImageMagick COMPONENTS Magick++)

include_directories(Boost::boost)
include_directories(${ImageMagick_INCLUDE_DIRS})

add_executable(main main.cpp)
add_definitions( -DMAGICKCORE_QUANTUM_DEPTH=16 )
add_definitions( -DMAGICKCORE_HDRI_ENABLE=0 )
target_link_libraries(main Boost::system Threads::Threads gmp ${ImageMagick_LIBRARIES})

set(TARGETS main)

set_property(TARGET ${TARGETS} PROPERTY CXX_STANDARD 17)
set_property(TARGET ${TARGETS} PROPERTY CXX_STANDARD_REQUIRED ON)
set_property(TARGET ${TARGETS} PROPERTY CXX_EXTENSION OFF)
