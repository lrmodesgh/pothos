########################################################################
# Network blocks module
########################################################################
#udt support
file(GLOB UDT_SOURCES RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/udt4/src/*.cpp)
add_definitions(-DUDT_EXPORTS)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/udt4/src)

if (WIN32)
    list(APPEND MODULE_LIBRARIES ws2_32)
endif (WIN32)

POTHOS_MODULE_UTIL(
    TARGET NetworkBlocks
    SOURCES
        ${UDT_SOURCES}
        NetworkSource.cpp
        NetworkSink.cpp
        SocketEndpoint.cpp
        TestNetworkBlocks.cpp
        TestNetworkTopology.cpp
    DESTINATION blocks
    LIBRARIES ${MODULE_LIBRARIES}
    ENABLE_DOCS
)
