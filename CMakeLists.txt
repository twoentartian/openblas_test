cmake_minimum_required(VERSION 3.23)

include("cmake/HunterGate.cmake")
HunterGate(
        URL "https://github.com/twoentartian/hunter/archive/refs/tags/test.tar.gz"
        SHA1 "05269beb951f506ecc0434e2efbb92e34c4d05b9"
        LOCAL
)

project(openblas)

set(CMAKE_CXX_STANDARD 20)

set(LINKER_LIBS)
hunter_add_package(OpenBLAS)
find_package(OpenBLAS CONFIG REQUIRED)
list(APPEND LINKER_LIBS OpenBLAS::OpenBLAS)

add_executable(openblas main.cpp)
target_link_libraries(openblas ${LINKER_LIBS})
