cmake_minimum_required(VERSION 3.10)
project(consensus LANGUAGES CXX)

# Use C++17 standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Optionally include common project defaults
if(EXISTS "${CMAKE_SOURCE_DIR}/cmake/ProjectDefaults.cmake")
    include("${CMAKE_SOURCE_DIR}/cmake/ProjectDefaults.cmake")
endif()

# Gather all source files for the consensus module
file(GLOB_RECURSE CONSENSUS_SOURCES
    "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/*.cxx"
    "${CMAKE_CURRENT_SOURCE_DIR}/*.cc"
)

# Create the consensus library and set include directories appropriately
if(CONSENSUS_SOURCES)
    add_library(consensus ${CONSENSUS_SOURCES})
    target_include_directories(consensus PUBLIC
        ${CMAKE_SOURCE_DIR}/include/protochain/consensus/core
        ${CMAKE_SOURCE_DIR}/include/protochain/consensus
    )
else()
    message(WARNING "No source files found for consensus. Creating INTERFACE library.")
    add_library(consensus INTERFACE)
    target_include_directories(consensus INTERFACE
        ${CMAKE_SOURCE_DIR}/include/protochain/consensus/core
        ${CMAKE_SOURCE_DIR}/include/protochain/consensus
    )
endif()

# Link additional libraries if necessary
# target_link_libraries(consensus <other_libraries>)

# Optionally add subdirectories for tests
# add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../../tests)
