cmake_minimum_required(VERSION 2.8)
set(platform x64)

set(CMAKE_SYSTEM_NAME Linux )

SET (CMAKE_C_COMPILER             "/opt/rh/llvm-toolset-7/root/usr/bin/clang")
SET (CMAKE_C_FLAGS                "-Wall -std=c99")
SET (CMAKE_C_FLAGS_DEBUG          "-g")
SET (CMAKE_C_FLAGS_MINSIZEREL     "-Os -DNDEBUG")
SET (CMAKE_C_FLAGS_RELEASE        "-O3 -DNDEBUG")
SET (CMAKE_C_FLAGS_RELWITHDEBINFO "-O2 -g")

SET (CMAKE_CXX_COMPILER             "/opt/rh/llvm-toolset-7/root/usr/bin/clang++")
SET (CMAKE_CXX_FLAGS                "-Wall -std=c++11")
SET (CMAKE_CXX_FLAGS_DEBUG          "-g")
SET (CMAKE_CXX_FLAGS_MINSIZEREL     "-Os -DNDEBUG")
SET (CMAKE_CXX_FLAGS_RELEASE        "-O3 -DNDEBUG")
SET (CMAKE_CXX_FLAGS_RELWITHDEBINFO "-O2 -g")


PROJECT(decnumber)

SET(DIR_SRCS ./src/decContext.c ./src/decDouble.c ./src/decNumber.c ./src/decPacked.c ./src/decQuad.c ./src/decSingle.c ./src/decimal128.c ./src/decimal32.c ./src/decimal64.c)

ADD_LIBRARY(${PROJECT_NAME} STATIC ${DIR_SRCS})

install(TARGETS ${PROJECT_NAME}
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib)

install(DIRECTORY src/ DESTINATION include/decnumber
    FILES_MATCHING PATTERN "*.h" PATTERN "*.c")

