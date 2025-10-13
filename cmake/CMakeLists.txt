cmake_minimum_required(VERSION 3.20)
project(protochain VERSION 0.0.1 LANGUAGES CXX)

# ── Options ────────────────────────────────────────────────────────────────────
option(ENABLE_SANITIZERS "Enable ASan/UBSan in Debug builds (non-MSVC)" ON)
option(BUILD_TESTS       "Build unit/integration tests"                   OFF)

# ── C++ standard & policies ────────────────────────────────────────────────────
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# ── Helper targets: warnings & sanitizers ─────────────────────────────────────
add_library(protochain_warnings INTERFACE)
if (MSVC)
  target_compile_options(protochain_warnings INTERFACE /W4 /permissive- /Zc:__cplusplus)
else()
  target_compile_options(protochain_warnings INTERFACE
    -Wall -Wextra -Wpedantic
    -Wconversion -Wshadow -Wnon-virtual-dtor
  )
endif()

add_library(protochain_sanitizers INTERFACE)
if (NOT MSVC AND ENABLE_SANITIZERS)
  target_compile_options(protochain_sanitizers INTERFACE -fsanitize=address,undefined)
  target_link_options   (protochain_sanitizers INTERFACE -fsanitize=address,undefined)
endif()

# ── Global defines for versioning & reproducible paths ────────────────────────
add_library(protochain_project_options INTERFACE)
target_compile_definitions(protochain_project_options INTERFACE PROTOCHAIN_VERSION="${PROJECT_VERSION}")
if (NOT MSVC)
  target_compile_options(protochain_project_options INTERFACE -ffile-prefix-map=${CMAKE_SOURCE_DIR}=.)
endif()

# ── Include dirs ───────────────────────────────────────────────────────────────
set(PROTOCHAIN_PUBLIC_INCLUDE ${CMAKE_CURRENT_SOURCE_DIR}/include)

# ── Subdirectories (modules) ───────────────────────────────────────────────────
add_subdirectory(src/core/types)
add_subdirectory(src/consensus)
add_subdirectory(src/node)

# ── Tests (позже наполним) ────────────────────────────────────────────────────
if (BUILD_TESTS)
  enable_testing()
  add_subdirectory(tests)
endif()
