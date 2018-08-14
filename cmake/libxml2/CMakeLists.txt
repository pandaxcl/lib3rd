get_filename_component(target ${CMAKE_CURRENT_LIST_DIR} NAME)

set(SOURCE_DIR ${LIB3RD_REPO_DOWNLOADED_DIR}/libxml2.git)

add_library(${target} STATIC "")


file(GLOB_RECURSE x ${SOURCE_DIR}/*.h ${SOURCE_DIR}/*.c)
file(GLOB_RECURSE os400  ${SOURCE_DIR}/os400/*)
file(GLOB_RECURSE win32  ${SOURCE_DIR}/win32/*)
file(GLOB_RECURSE doc    ${SOURCE_DIR}/doc/*)
file(GLOB_RECURSE python ${SOURCE_DIR}/python/*)
file(GLOB_RECURSE macos  ${SOURCE_DIR}/macos/*)
file(GLOB_RECURSE y      ${SOURCE_DIR}/trio.h 
                         ${SOURCE_DIR}/trio.c 
                         ${SOURCE_DIR}/include/libxml/threads.h 
                         ${SOURCE_DIR}/threads.c 
                         ${SOURCE_DIR}/test*.c)
list(REMOVE_ITEM x ${y} ${os400} ${win32} ${doc} ${python} ${macos})

list(APPEND sources ${x})

target_sources(${target} PRIVATE ${sources})
source_group(TREE ${SOURCE_DIR} FILES ${sources})


target_include_directories(${target} PUBLIC ${SOURCE_DIR}/include)
#target_include_directories(${target} PUBLIC ${SOURCE_DIR})
set_target_properties(${target} PROPERTIES FOLDER gift_lib3rd)
