cmake_minimum_required(VERSION 3.14)

project(jni-read-dicekey
    VERSION 0.11
    DESCRIPTION "JNI Library."
    LANGUAGES CXX
)

# 🔹 Apply 16 KB page-size linker flag globally to ALL shared libs
set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} -Wl,-z,max-page-size=16384")
set(CMAKE_MODULE_LINKER_FLAGS "${CMAKE_MODULE_LINKER_FLAGS} -Wl,-z,max-page-size=16384")

add_subdirectory("read-dicekey")

add_library(
    jni-read-dicekey
    SHARED
    "read-dicekey-jni.cpp"
)

target_link_libraries( jni-read-dicekey
    PRIVATE
    lib-read-dicekey
    lib-dicekey
)
