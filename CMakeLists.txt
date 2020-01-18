cmake_minimum_required(VERSION 3.12)

project(foo CXX)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# nlohmann_json
set(JSON_BuildTests OFF CACHE INTERNAL "")
set(JSON_Install    OFF CACHE INTERNAL "")
add_subdirectory(nlohmann_json)

# json-schema-validator
set(BUILD_TESTS OFF CACHE BOOL "")
set(BUILD_EXAMPLES OFF CACHE BOOL "")
add_subdirectory(json_schema_validator)

add_executable(foo main.cc)
target_link_libraries(foo nlohmann_json::nlohmann_json nlohmann_json_schema_validator)
