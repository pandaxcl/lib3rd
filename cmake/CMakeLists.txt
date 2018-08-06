cmake_minimum_required(VERSION 3.12)

#set(LIB3RD_HOME_DIR ${HOME}/gift/lib3rd.downloaded)
set(LIB3RD_HOME_DIR /Users/pandaxcl/gift/lib3rd.downloaded)

project(lib3rd.downloaded)
add_subdirectory(boost_1_67_0)
add_subdirectory(zeromq-4.2.3)
add_subdirectory(cppzmq)

