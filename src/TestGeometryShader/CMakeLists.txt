set(APP_NAME TestGeometryShader)

file(GLOB CoreFiles *.cpp *.h)

set(SourceFiles ${CoreFiles})

SOURCE_GROUP("Source Files" FILES ${CoreFiles})

include_directories(..)

find_package(Boost COMPONENTS thread regex system filesystem program_options REQUIRED)
include_directories(${Boost_INCLUDE_DIRS})
link_directories(${Boost_LIBRARY_DIRS})

find_package(GAppFramework)
include_directories(${GAppFramework_INCLUDE_DIRS} ${Boost_INCLUDE_DIRS})

add_executable(${APP_NAME} ${SourceFiles})

target_link_libraries (${APP_NAME} ${GAppFramework_LIBRARIES} ${Boost_LIBRARIES})
