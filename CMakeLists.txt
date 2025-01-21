cmake_minimum_required(VERSION 3.10)
project(PurePursuit)

# C++ standardını belirtiyoruz
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Boost'u bul ve dahil et
set(BOOST_ROOT "/home/basaran/Masaüstü/PurePursuit/lib/boost_1_82_0")
set(BOOST_INCLUDEDIR "${BOOST_ROOT}/include")
set(BOOST_LIBRARYDIR "${BOOST_ROOT}/lib")
find_package(Boost REQUIRED)
include_directories(${BOOST_INCLUDEDIR})

# Python ve matplotlib için gerekli ayarlar
find_package(Python3 COMPONENTS Interpreter Development NumPy REQUIRED)
include_directories(${Python3_INCLUDE_DIRS} ${Python3_NumPy_INCLUDE_DIRS})

# NumPy'nin doğru şekilde bulunduğunu kontrol et
if(NOT Python3_NumPy_FOUND)
    message(FATAL_ERROR "Python NumPy kütüphanesi bulunamadı!")
endif()

# matplotlib-cpp'nin yolunu belirt
set(MATPLOTLIB_CPP_DIR "/home/basaran/Masaüstü/PurePursuit/lib/matplotlib-cpp")
include_directories(${MATPLOTLIB_CPP_DIR})

# Derleme hedeflerini ayarla
add_executable(pure_pursuit pure_pursuit.cpp)

# Python ve Boost kütüphanelerini linkle
target_link_libraries(pure_pursuit Python3::Python ${Boost_LIBRARIES})
