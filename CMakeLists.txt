cmake_minimum_required(VERSION 2.8)

#设置编译器
IF (CMAKE_COMPILER_TYPE MATCHES "GCC")
    SET(CMAKE_C_COMPILER "gcc")
    SET(CMAKE_CXX_COMPILER "g++")
ELSEIF (CMAKE_COMPILER_TYPE MATCHES "CLANG")
    SET(CMAKE_C_COMPILER "clang")
    SET(CMAKE_CXX_COMPILER "clang++")
ENDIF ()

SET(CMAKE_C_FLAGS "-Wall -std=c99")
SET(CMAKE_C_FLAGS_DEBUG "-g")
SET(CMAKE_C_FLAGS_MINSIZEREL "-Os -DNDEBUG")
SET(CMAKE_C_FLAGS_RELEASE "-O3 -DNDEBUG")
SET(CMAKE_C_FLAGS_RELWITHDEBINFO "-O2 -g")

SET(CMAKE_CXX_FLAGS "-Wall -std=c++11")
SET(CMAKE_CXX_FLAGS_DEBUG "-g")
SET(CMAKE_CXX_FLAGS_MINSIZEREL "-Os -DNDEBUG")
SET(CMAKE_CXX_FLAGS_RELEASE "-O3 -DNDEBUG")
SET(CMAKE_CXX_FLAGS_RELWITHDEBINFO "-O2 -g")


#判断操作系统
IF (WIN32)
    MESSAGE(STATUS "Now is windows")
ELSEIF (APPLE)
    MESSAGE(STATUS "Now is Apple systens.")
ELSEIF (UNIX)
    MESSAGE(STATUS "Now is UNIX-like OS's. Including aPPLE os x  and CygWin")
ENDIF ()

if (UNIX AND NOT APPLE)
    set(platform x64)
    set(LINUX TRUE)
endif ()

if (APPLE)
endif ()


if (LINUX)
    message(STATUS "当前操作系统: Linux")
endif ()

if (APPLE)
    message(STATUS "当前操作系统: MacOS")
endif ()

MESSAGE(STATUS "operation system is ${CMAKE_SYSTEM}")


PROJECT(decnumber)

SET(DIR_SRCS ./src/decContext.c ./src/decDouble.c ./src/decNumber.c ./src/decPacked.c ./src/decQuad.c ./src/decSingle.c ./src/decimal128.c ./src/decimal32.c ./src/decimal64.c)

ADD_LIBRARY(${PROJECT_NAME} STATIC ${DIR_SRCS})

install(TARGETS ${PROJECT_NAME}
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib)

install(DIRECTORY src/ DESTINATION include/decnumber
    FILES_MATCHING PATTERN "*.h" PATTERN "*.c")

