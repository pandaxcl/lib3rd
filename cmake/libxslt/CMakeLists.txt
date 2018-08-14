get_filename_component(target ${CMAKE_CURRENT_LIST_DIR} NAME)

set(SOURCE_DIR ${LIB3RD_REPO_DOWNLOADED_DIR}/libxslt.git)

add_library(${target} STATIC "")


file(GLOB_RECURSE x ${SOURCE_DIR}/libxslt/*.h ${SOURCE_DIR}/libxslt/*.c)
#list(REMOVE_ITEM x random.hpp random.cpp)
list(APPEND sources ${x})

file(GLOB_RECURSE x ${SOURCE_DIR}/libexslt/*.h ${SOURCE_DIR}/libexslt/*.c)
#list(REMOVE_ITEM x random.hpp random.cpp)
list(APPEND sources ${x})

target_sources(${target} PRIVATE ${sources})
source_group(TREE ${SOURCE_DIR} FILES ${sources})


target_include_directories(${target} PUBLIC ${SOURCE_DIR})

target_link_libraries(${target} PUBLIC libxml2)
set_target_properties(${target} PROPERTIES FOLDER gift_lib3rd)
