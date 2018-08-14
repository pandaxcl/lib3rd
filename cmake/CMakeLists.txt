cmake_minimum_required(VERSION 3.12)

#set(LIB3RD_HOME_DIR ${HOME}/gift/lib3rd.downloaded)
set(LIB3RD_HOME_DIR /Users/pandaxcl/gift/lib3rd.downloaded)
set(LIB3RD_REPO_DIR ${CMAKE_CURRENT_LIST_DIR}/..)
set(LIB3RD_REPO_DOWNLOADED_DIR ${LIB3RD_REPO_DIR}/lib3rd.downloaded)

project(lib3rd.downloaded)
add_subdirectory(boost_1_67_0)
add_subdirectory(zeromq-4.2.3)
add_subdirectory(cppzmq)
add_subdirectory(catch2)
add_subdirectory(rxcpp)
add_subdirectory(cpplinq)
add_subdirectory(libxml2)
add_subdirectory(libxslt)

add_library(lib3rd.downloaded STATIC "")
target_sources(lib3rd.downloaded PRIVATE ../lib3rd/lib3rd.cpp)
target_link_libraries(lib3rd.downloaded PUBLIC
	boost_1_67_0
	zeromq-4.2.3
	cppzmq
	catch2
	rxcpp
	cpplinq
	libxml2
	libxslt
)
