get_filename_component(target ${CMAKE_CURRENT_LIST_DIR} NAME)

set(SOURCE_DIR ${LIB3RD_REPO_DIR}/lib3rd.downloaded/boost_1_67_0)


add_library(${target} STATIC "")

file(GLOB_RECURSE x ${SOURCE_DIR}/libs/serialization/src/*.cpp)
list(APPEND sources ${x})

file(GLOB_RECURSE x ${SOURCE_DIR}/libs/system/src/*.cpp)
list(APPEND sources ${x})

file(GLOB_RECURSE x ${SOURCE_DIR}/libs/filesystem/src/*.cpp)
list(APPEND sources ${x})

#file(GLOB_RECURSE x ${SOURCE_DIR}/libs/math/src/*.cpp)
#list(APPEND sources ${x})

#file(GLOB_RECURSE x ${SOURCE_DIR}/libs/mpi/src/*.cpp)
#list(APPEND sources ${x})

file(GLOB_RECURSE x ${SOURCE_DIR}/libs/program_options/src/*.cpp)
list(APPEND sources ${x})

file(GLOB_RECURSE x ${SOURCE_DIR}/libs/regex/src/*.cpp)
list(APPEND sources ${x})


source_group(TREE ${SOURCE_DIR} FILES ${sources})
target_sources(${target} PRIVATE ${sources})

target_include_directories(${target} PUBLIC ${SOURCE_DIR})
