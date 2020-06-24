cmake_minimum_required(VERSION 3.0)

project(recast_navigation)

find_package(catkin)

catkin_package(
INCLUDE_DIRS DebugUtils/Include Detour/Include DetourTileCache/Include DetourCrowd/Include Recast/Include RecastDemo/Contrib/fastlz
LIBRARIES ${PROJECT_NAME}
)

# lib versions
SET(SOVERSION 1)
SET(VERSION 1.0.0)

option(RECASTNAVIGATION_DEMO "Build demo" ON)
option(RECASTNAVIGATION_TESTS "Build tests" ON)
option(RECASTNAVIGATION_EXAMPLES "Build examples" ON)
option(RECASTNAVIGATION_STATIC "Build static libraries" ON)

#add_subdirectory(DebugUtils)
#add_subdirectory(Detour)
#add_subdirectory(DetourCrowd)
#add_subdirectory(DetourTileCache)
#add_subdirectory(Recast)

#if (RECASTNAVIGATION_DEMO)
#    add_subdirectory(RecastDemo)
#endif ()

set(RECAST_INCLUDE_DIRS
  DebugUtils/Include
  Detour/Include
  DetourTileCache/Include
  DetourCrowd/Include
  Recast/Include
  RecastDemo/Contrib/fastlz
)
include_directories(${RECAST_INCLUDE_DIRS})

file(GLOB RecastSources
  DebugUtils/Source/*.cpp
  Detour/Source/*.cpp
  DetourTileCache/Source/*.cpp
  DetourCrowd/Source/*.cpp
  Recast/Source/*.cpp
  Recast/Source/*.c
  RecastDemo/Contrib/fastlz/*.c
)

add_library(${PROJECT_NAME}
  ${RecastSources}
)

