get_filename_component(target ${CMAKE_CURRENT_LIST_DIR} NAME)

set(SOURCE_DIR ${CMAKE_CURRENT_LIST_DIR}/../../cppzmq-master)

add_library(${target} INTERFACE)

target_include_directories(${target} INTERFACE ${SOURCE_DIR})
#set_target_properties(${target} PROPERTIES FOLDER gift_lib3rd)
