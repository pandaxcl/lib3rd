cmake_minimum_required(VERSION 3.11)

set(LIB3RD_REPO_DIR ${CMAKE_CURRENT_LIST_DIR})
set(LIB3RD_REPO_DOWNLOADED_DIR ${LIB3RD_REPO_DIR}/lib3rd.downloaded)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_OSX_DEPLOYMENT_TARGET "10.9" CACHE STRING "Minimum OS X deployment version")

project(lib3rd.downloaded)
add_subdirectory(cmake)
#add_subdirectory(${LIB3RD_REPO_DOWNLOADED_DIR}/libzmq.git)
#set_target_properties(objects PROPERTIES PREFIX "libzmp_")
#set_target_properties(objects PROPERTIES OUTPUT_NAME "better_name")
#set_target_properties(objects PROPERTIES SUFFIX ".so.1")
