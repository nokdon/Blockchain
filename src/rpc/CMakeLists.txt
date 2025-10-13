# Minimal CMakeLists for rpc module
if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/jsonrpc/CMakeLists.txt")
    add_subdirectory(jsonrpc)
endif()
