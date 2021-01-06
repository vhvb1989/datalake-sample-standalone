cmake_minimum_required (VERSION 3.13)

# VCPKG Integration (https://github.com/microsoft/vcpkg/blob/master/docs/users/integration.md)
if(DEFINED ENV{VCPKG_ROOT} AND NOT DEFINED CMAKE_TOOLCHAIN_FILE)
  set(CMAKE_TOOLCHAIN_FILE "$ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake" CACHE STRING "")
elseif(DEFINED ENV{VCPKG_INSTALLATION_ROOT} AND NOT DEFINED CMAKE_TOOLCHAIN_FILE)
  set(CMAKE_TOOLCHAIN_FILE "$ENV{VCPKG_INSTALLATION_ROOT}/scripts/buildsystems/vcpkg.cmake" CACHE STRING "")
endif()
if(DEFINED ENV{VCPKG_DEFAULT_TRIPLET} AND NOT DEFINED VCPKG_TARGET_TRIPLET)
  set(VCPKG_TARGET_TRIPLET "$ENV{VCPKG_DEFAULT_TRIPLET}" CACHE STRING "")
endif()

# Project definition
project(datalake-sample-standalone LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED True)

if(MSVC)
  add_compile_options(/MTd)
endif()

# vcpkg install azure-storage-files-datalake-cpp
# vcpkg install azure-storage-files-datalake-cpp:x64-windows-static
find_package(azure-storage-files-datalake-cpp CONFIG REQUIRED)
add_executable(datalake_sample_standalone datalake_sample_standalone.cpp)
target_link_libraries(datalake_sample_standalone PRIVATE Azure::azure-storage-files-datalake)
