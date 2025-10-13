# Minimal CMakeLists for net module
if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/discovery/CMakeLists.txt")
    add_subdirectory(discovery)
endif()

if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/p2p/CMakeLists.txt")
    add_subdirectory(p2p)
endif()

if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/pubsub/CMakeLists.txt")
    add_subdirectory(pubsub)
endif()

if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/transport/CMakeLists.txt")
    add_subdirectory(transport)
endif()
