cmake_minimum_required(VERSION 2.8)
project(libpqmxx)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/Modules/")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread -std=c++14")
#aux_source_directory(. SRC_LIST)
#add_executable(${PROJECT_NAME} ${SRC_LIST})

SET(PG_BASE "/usr")
SET(SOURCE_FILES
        src/postgres-connection.cpp
		src/postgres-params.cpp
		src/postgres-result.cpp
        )

add_library(${PROJECT_NAME} ${SOURCE_FILES})
SET(LIBRARY_OUTPUT_PATH lib)
INCLUDE_DIRECTORIES("${PG_BASE}/include/postgresql"
					"include"
                   )
LINK_DIRECTORIES("${PG_BASE}/lib/postgresql")
TARGET_LINK_LIBRARIES(${PROJECT_NAME} "${PG_BASE}/lib/libpq.so")