# src/core/types/CMakeLists.txt
add_library(protochain_core_types STATIC
  ${CMAKE_CURRENT_SOURCE_DIR}/../../..//include/protochain/core/types/types.hpp
  ${CMAKE_CURRENT_SOURCE_DIR}/types.cpp
)

target_include_directories(protochain_core_types
  PUBLIC ${PROTOCHAIN_PUBLIC_INCLUDE}
)

target_link_libraries(protochain_core_types
  PUBLIC protochain_warnings protochain_project_options protochain_sanitizers
)

set_target_properties(protochain_core_types PROPERTIES OUTPUT_NAME "core_types")
