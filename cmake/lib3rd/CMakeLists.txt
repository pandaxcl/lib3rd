get_filename_component(target ${CMAKE_CURRENT_LIST_DIR} NAME)

set(SOURCE_DIR ${LIB3RD_REPO_DIR}/lib3rd)

add_library(${target} STATIC "")


file(GLOB_RECURSE x ${SOURCE_DIR}/*.hpp ${SOURCE_DIR}/*.cpp)
#list(REMOVE_ITEM x loslib.c) // iOS has no function named: system
list(APPEND sources ${x})

target_sources(${target} PRIVATE ${sources})
source_group(TREE ${SOURCE_DIR} FILES ${sources})

target_include_directories(${target}
    PUBLIC ${SOURCE_DIR}/include
    #PRIVATE ${SOURCE_DIR}/src ${LIB3RD_REPO_DOWNLOADED_DIR}/boost_1_69_0 
)
set_target_properties(${target} PROPERTIES FOLDER gift_lib3rd)


