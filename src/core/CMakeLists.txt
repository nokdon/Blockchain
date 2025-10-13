# Minimal CMakeLists for core module
if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/types/CMakeLists.txt")
    add_subdirectory(types)
endif()

if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/crypto/CMakeLists.txt")
    add_subdirectory(crypto)
endif()
