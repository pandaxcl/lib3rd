get_filename_component(target ${CMAKE_CURRENT_LIST_DIR} NAME)

set(SOURCE_DIR ${LIB3RD_REPO_DIR}/lib3rd.downloaded/yoga.git)

add_library(${target} STATIC "")


file(GLOB_RECURSE x ${SOURCE_DIR}/yoga/*.h ${SOURCE_DIR}/yoga/*.hpp ${SOURCE_DIR}/yoga/*.cpp)
#list(REMOVE_ITEM x random.hpp random.cpp)
list(APPEND sources ${x})
#file(GLOB_RECURSE x ${SOURCE_DIR}/include/*.hpp)
#list(APPEND sources ${x})

target_sources(${target} PRIVATE ${sources})
source_group(TREE ${SOURCE_DIR} FILES ${sources})

target_include_directories(${target}
    PUBLIC ${SOURCE_DIR}
    PRIVATE ${SOURCE_DIR}/yoga
)
set_target_properties(${target} PROPERTIES FOLDER gift_lib3rd)


