cmake_minimum_required(VERSION 3.10)

# Проект Blockchain
project(Blockchain LANGUAGES CXX)

# Установка стандарта C++
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Опционально: подключение общих настроек проекта, если существует
if(EXISTS "${CMAKE_SOURCE_DIR}/cmake/ProjectDefaults.cmake")
    include("${CMAKE_SOURCE_DIR}/cmake/ProjectDefaults.cmake")
endif()

# Добавление подпроектов
add_subdirectory(src/consensus)
add_subdirectory(src/core)
add_subdirectory(src/net)
add_subdirectory(src/node)
add_subdirectory(src/rpc)
add_subdirectory(src/storage)
add_subdirectory(src/vm)

# Опционально можно добавить тесты и другие модули
# add_subdirectory(tests)
