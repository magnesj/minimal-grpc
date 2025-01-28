cmake_minimum_required(VERSION 3.15)

# Project name
project(GrpcProject VERSION 1.0 LANGUAGES CXX)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add vcpkg toolchain file
if(DEFINED ENV{VCPKG_ROOT})
    set(CMAKE_TOOLCHAIN_FILE "$ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake" CACHE STRING "Vcpkg toolchain file")
else()
    message(FATAL_ERROR "VCPKG_ROOT environment variable is not set.")
endif()

# Find gRPC package
find_package(gRPC CONFIG REQUIRED)

# Add the executable
add_executable(grpc_project main.cpp)

# Link gRPC libraries
#if(TARGET gRPC::grpc++_reflection)
#    target_link_libraries(grpc_project PRIVATE gRPC::grpc++ gRPC::grpc++_reflection)
#else()
#    target_link_libraries(grpc_project PRIVATE gRPC::grpc++)
#endif()

# Include directories
include_directories(${CMAKE_SOURCE_DIR})
