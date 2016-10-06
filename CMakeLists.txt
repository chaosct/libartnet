cmake_minimum_required(VERSION 2.8)

project (artnet)

# Find source files
set(SOURCE_FILES
        artnet/artnet.c
        artnet/artnet.h
        artnet/common.h
        artnet/misc.c
        artnet/misc.h
        artnet/network.c
        artnet/packets.h
        artnet/private.h
        artnet/receive.c
        artnet/tod.c
        artnet/tod.h
        artnet/transmit.c
        )

include_directories(
      .
)

# Use @rpath for install name
set(CMAKE_MACOSX_RPATH 1)

# Create shared library
add_library(${PROJECT_NAME} SHARED ${SOURCE_FILES})

# Install library
install(TARGETS ${PROJECT_NAME} DESTINATION lib/${PROJECT_NAME})

# Install library headers
file(GLOB HEADERS artnet/*.h)
install(FILES ${HEADERS} DESTINATION include/${PROJECT_NAME})