get_filename_component(target ${CMAKE_CURRENT_LIST_DIR} NAME)

set(SOURCE_DIR ${LIB3RD_HOME_DIR}/zeromq-4.2.3)

add_library(${target} STATIC "")


file(GLOB_RECURSE x ${SOURCE_DIR}/src/*.hpp ${SOURCE_DIR}/src/*.cpp)
list(APPEND sources ${x})

target_sources(${target} PRIVATE ${sources})


target_include_directories(${target} PUBLIC ${SOURCE_DIR}/include)
set_target_properties(${target} PROPERTIES FOLDER gift_lib3rd)
