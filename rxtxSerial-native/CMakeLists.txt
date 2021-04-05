cmake_minimum_required(VERSION 3.17)
project(rxtxSerial_native C)

set(CMAKE_C_STANDARD 99)
set(JAVA_HOME_PATH /usr/lib/jvm/java-14-openjdk-amd64)

add_library(rxtxSerial_native SHARED
        src/main/c/SerialImp.c
        src/main/c/SerialImp.h
        )
target_include_directories(rxtxSerial_native
        PRIVATE ../rxtxSerial-java/target/headers
        PRIVATE ${JAVA_HOME_PATH}/include
        PRIVATE ${JAVA_HOME_PATH}/include/linux
        )
target_compile_definitions(rxtxSerial_native PRIVATE
        HAVE_TERMIOS_H
        HAVE_STDINT_H
        HAVE_SYS_FCNTL_H
        HAVE_SYS_SIGNAL_H
        )
