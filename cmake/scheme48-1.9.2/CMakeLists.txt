get_filename_component(target ${CMAKE_CURRENT_LIST_DIR} NAME)

set(SOURCE_DIR ${LIB3RD_REPO_DIR}/lib3rd.downloaded/scheme.gift/scheme48-1.9.2/c)

add_library(${target} STATIC "")


file(GLOB_RECURSE x ${SOURCE_DIR}/*.h ${SOURCE_DIR}/*.c)

file(GLOB_RECURSE y ${SOURCE_DIR}/win32/*.h ${SOURCE_DIR}/win32/*.c)
list(REMOVE_ITEM x ${y})
file(GLOB_RECURSE y ${SOURCE_DIR}/unix/*.h ${SOURCE_DIR}/unix/*.c)
list(REMOVE_ITEM x ${y})
file(GLOB_RECURSE y ${SOURCE_DIR}/script-interpreter.c main.c)
list(REMOVE_ITEM x ${y})
file(GLOB_RECURSE y ${SOURCE_DIR}/*-32.c)
list(REMOVE_ITEM x ${y})

list(APPEND sources ${x})

target_sources(${target} PRIVATE ${sources})
source_group(TREE ${SOURCE_DIR} FILES ${sources})

target_include_directories(${target}
    PRIVATE ${SOURCE_DIR}
    #PRIVATE ${SOURCE_DIR}/src ${LIB3RD_REPO_DOWNLOADED_DIR}/boost_1_69_0 
)
set_target_properties(${target} PROPERTIES FOLDER gift_lib3rd)

target_compile_definitions(${target} PUBLIC -D S48_HOST_ARCHITECTURE="XCL")
#target_compile_definitions(${target} PUBLIC -D NO_OLD_FFI)
target_compile_definitions(${target} PUBLIC -D STATIC_AREAS)
