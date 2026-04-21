cmake_minimum_required(VERSION 4.3)
project(std-cli CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

include(FetchContent)
set(FETCHCONTENT_BASE_DIR "${CMAKE_SOURCE_DIR}/.deps")

FetchContent_Declare(
  CLI11
  GIT_REPOSITORY https://github.com/CLIUtils/CLI11.git
  GIT_TAG        v2.6.2
)
FetchContent_Declare(
  nlohmann_json
  GIT_REPOSITORY https://github.com/nlohmann/json.git
  GIT_TAG        v3.12.0
)

FetchContent_MakeAvailable(CLI11 nlohmann_json)

add_executable(std-cli src/main.cpp)

target_link_libraries(std-cli PRIVATE
  CLI11::CLI11
  nlohmann_json::nlohmann_json
)



