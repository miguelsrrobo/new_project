# This basic file is used to compile the runtime for the Editor preview.

if (CMAKE_SOURCE_DIR STREQUAL CMAKE_CURRENT_SOURCE_DIR)
  cmake_minimum_required(VERSION 3.10)
  project(LVGLProject)
  set(IS_TOP_LEVEL TRUE)
else()
  set(IS_TOP_LEVEL FALSE)
endif()

include(${CMAKE_CURRENT_LIST_DIR}/file_list_gen.cmake)

add_library(lib-ui ${PROJECT_SOURCES})

# 👇 FIX CRÍTICO
add_library(lvgl INTERFACE)

target_include_directories(lib-ui PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

if (LV_EDITOR_PREVIEW)
    # Preview
else ()
    # Target real (ESP32, etc)
endif ()
