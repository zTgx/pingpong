SET(PROJECTNAME ssl_server)
project(${PROJECTNAME})
cmake_minimum_required(VERSION 3.1)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS} O0 -Wall -g -ggdb")

#ssl
INCLUDE_DIRECTORIES(/usr/local/ssl/include)
LINK_DIRECTORIES(/usr/local/ssl/lib)

add_executable(ssl_server server.cpp)


FIND_PACKAGE(Boost 1.57.0 COMPONENTS thread date_time filesystem system log log_setup REQUIRED)
INCLUDE_DIRECTORIES(${BOOST_ROOT})
LINK_LIBRARIES(${PROJECTNAME} ${BOOST_ROOT})

#AUX_SOURCE_DIRECTORY(./ DIR_SERVER_SRCS)
#add_executable(${PROJECTNAME} server.cpp)

#ssl
target_link_libraries(${PROJECTNAME} libssl.a)
target_link_libraries(${PROJECTNAME} libcrypto.a)
target_link_libraries(${PROJECTNAME} -ldl)

#boost
TARGET_LINK_LIBRARIES(${PROJECTNAME} libboost_log_setup.a)
TARGET_LINK_LIBRARIES(${PROJECTNAME} libboost_log.a)
TARGET_LINK_LIBRARIES(${PROJECTNAME} libboost_system.a)
TARGET_LINK_LIBRARIES(${PROJECTNAME} libboost_date_time.a)
TARGET_LINK_LIBRARIES(${PROJECTNAME} libboost_filesystem.a)
TARGET_LINK_LIBRARIES(${PROJECTNAME} libboost_thread.a)
TARGET_LINK_LIBRARIES(${PROJECTNAME} -lpthread)


