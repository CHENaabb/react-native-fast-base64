cmake_minimum_required(VERSION 3.9.0)

project(fastbase64)

set (CMAKE_VERBOSE_MAKEFILE ON)
set (CMAKE_CXX_STANDARD 17)

include_directories(
  "${NODE_MODULES_DIR}/react-native/React"
  "${NODE_MODULES_DIR}/react-native/React/Base"
  "${NODE_MODULES_DIR}/react-native/ReactCommon/jsi"
  ../cpp
)
cmake_path(CONVERT   "${NODE_MODULES_DIR}/react-native/ReactCommon/jsi/jsi/jsi.cpp" TO_CMAKE_PATH_LIST N0)
cmake_path(CONVERT "../cpp/Base64.cpp" TO_CMAKE_PATH_LIST N1)
cmake_path(CONVERT "../cpp/Base64.h" TO_CMAKE_PATH_LIST N2)
cmake_path(CONVERT "../cpp/react-native-fast-base64.cpp" TO_CMAKE_PATH_LIST N3)
cmake_path(CONVERT "../cpp/react-native-fast-base64.h" TO_CMAKE_PATH_LIST N4)
cmake_path(CONVERT "./cpp-adapter.cpp" TO_CMAKE_PATH_LIST N5)

add_library(fastbase64
  SHARED
  ${N0}
  ${N1}
  ${N2}
  ${N3}
  ${N4}
  ${N5}
)

target_link_libraries(fastbase64)
