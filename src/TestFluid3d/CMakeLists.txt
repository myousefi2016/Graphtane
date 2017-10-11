set(APP_NAME TestFluid3d)

file(GLOB CoreFiles *.cpp *.h)

set(SourceFiles ${CoreFiles} ${GVisFiles} ${PrimitivesFiles})

SOURCE_GROUP("Source Files" FILES ${CoreFiles})

include_directories(..)

find_package(Boost COMPONENTS thread regex system filesystem program_options REQUIRED)
include_directories(${Boost_INCLUDE_DIRS})
link_directories(${Boost_LIBRARY_DIRS})

find_package(GAppFramework)
include_directories(${GAppFramework_INCLUDE_DIRS})

find_package(GCompute)
include_directories(${GCompute_INCLUDE_DIRS})

add_executable(${APP_NAME} ${SourceFiles})

target_link_libraries (${APP_NAME} ${GCompute_LIBRARIES} GFluid GComputeVis ${GAppFramework_LIBRARIES} ${Boost_LIBRARIES})
