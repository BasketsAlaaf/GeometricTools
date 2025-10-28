if(COMMAND cmake_policy)
    # Allow VERSION in the project() statement.
    cmake_policy(SET CMP0048 NEW)
endif()

cmake_minimum_required(VERSION 3.8)

set(GTE_VERSION_MAJOR 7)
set(GTE_VERSION_MINOR 3)
set(PROJECT_SOURCE_DIR ${CMAKE_CURRENT_LIST_DIR})

project(GTE VERSION ${GTE_VERSION_MAJOR}.${GTE_VERSION_MINOR})

option(BUILD_HEADER_ONLY "Compile the library" OFF)

if(NOT BUILD_HEADER_ONLY)
  add_subdirectory(Applications)
  add_subdirectory(Graphics)
  add_subdirectory(MathematicsGPU)
endif()

add_subdirectory(Mathematics)

option(BUILD_SAMPLES "Build Samples" OFF)
if(BUILD_SAMPLES)
  add_subdirectory(Samples)
endif()
