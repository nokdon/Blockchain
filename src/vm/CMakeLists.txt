# Minimal CMakeLists for vm module
if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/wasm/CMakeLists.txt")
    add_subdirectory(wasm)
endif()
