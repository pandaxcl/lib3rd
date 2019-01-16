get_filename_component(target ${CMAKE_CURRENT_LIST_DIR} NAME)

set(SOURCE_DIR ${LIB3RD_REPO_DIR}/lib3rd.downloaded/scheme.gift/minischeme-0.85k4.git/minischeme)

add_library(${target} STATIC "")


file(GLOB_RECURSE x ${SOURCE_DIR}/*.h ${SOURCE_DIR}/*.c)
#list(REMOVE_ITEM x loslib.c)
list(APPEND sources ${x})

target_sources(${target} PRIVATE ${sources})
source_group(TREE ${SOURCE_DIR} FILES ${sources})

target_include_directories(${target}
    PUBLIC ${SOURCE_DIR}/src
    #PRIVATE ${SOURCE_DIR}/src ${LIB3RD_REPO_DOWNLOADED_DIR}/boost_1_69_0 
)
set_target_properties(${target} PROPERTIES FOLDER gift_lib3rd)

target_compile_definitions(${target} PUBLIC -DSTANDALONE=0)
