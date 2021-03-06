# Copyright (C) 2018-2020 Intel Corporation
# SPDX-License-Identifier: Apache-2.0
#

find_package(InferenceEngine 2.0 REQUIRED)
find_package(OpenCV REQUIRED COMPONENTS core imgcodecs videoio)

file(GLOB_RECURSE HEADERS "${CMAKE_CURRENT_SOURCE_DIR}/include/*")
file(GLOB_RECURSE SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/src/*")

source_group("src" FILES ${SOURCES})
source_group("include" FILES ${HEADERS})

add_library(utils STATIC ${HEADERS} ${SOURCES})
target_include_directories(utils PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include")
target_link_libraries(utils PRIVATE gflags ${InferenceEngine_LIBRARIES} opencv_core opencv_imgcodecs opencv_videoio)
