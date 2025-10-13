# Minimal CMakeLists for storage module
if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/rocksdb/CMakeLists.txt")
    add_subdirectory(rocksdb)
endif()
