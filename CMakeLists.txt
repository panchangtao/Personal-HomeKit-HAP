cmake_minimum_required(VERSION 3.5)
project(homekit)

SET(CMAKE_BUILD_TYPE "Debug")
SET(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -O0 -Wall -g -ggdb")
SET(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -O3 -Wall")

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -m32")
include_directories(Chacha20         curve25519 ed25519-donna poly1305-opt-master  rfc6234-master   srp
        )
include_directories(/usr/include/sys)


set(SOURCE_FILES  Accessory.cpp  main.cpp  PHKAccessory.cpp  PHKControllerRecord.cpp  PHKNetworkIP.cpp
        Chacha20/chacha20_simple.c
        ed25519-donna/ed25519.c
        rfc6234-master/hkdf.c  rfc6234-master/hmac.c  rfc6234-master/sha.c
        poly1305-opt-master/poly1305.c
        srp/cstr.c  srp/srp6_server.c  srp/srp.c  srp/t_conf.c  srp/t_conv.c  srp/t_math.c  srp/t_misc.c  srp/t_pw.c  srp/t_read.c  srp/t_truerand.c
        curve25519/curve25519-donna.c
        )

add_executable(light_bulb ${SOURCE_FILES} )
