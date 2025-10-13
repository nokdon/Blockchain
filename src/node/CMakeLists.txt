# src/node/CMakeLists.txt
add_executable(node
  ${CMAKE_CURRENT_SOURCE_DIR}/main.cpp
)

target_include_directories(node PRIVATE ${PROTOCHAIN_PUBLIC_INCLUDE})

target_link_libraries(node
  PRIVATE protochain_consensus protochain_core_types
          protochain_warnings protochain_project_options protochain_sanitizers
)
