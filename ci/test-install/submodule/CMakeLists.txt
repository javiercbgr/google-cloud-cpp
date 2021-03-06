# Copyright 2019 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License"); you may not
# use this file except in compliance with the License. You may obtain a copy of
# the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
# WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the
# License for the specific language governing permissions and limitations under
# the License.

# A minimal CMakeList.txt to *test* using Cloud Bigtable C++ client as a
# submodule.
#
# This is not intended to be a demonstration of how to write good CMakeList.txt
# files, nor is it a general solution to create CMake files for google-cloud-
# cpp. It is simply a minimal CMake file to verify that when including the
# library as a submodule, that (a) the libraries contain all required headers,
# and (b) linking against the library works.

cmake_minimum_required(VERSION 3.5)
project(google-cloud-cpp-submodule-integration-test CXX C)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(google-cloud-cpp EXCLUDE_FROM_ALL)

add_executable(bigtable_install_test ../bigtable_install_test.cc)
target_link_libraries(bigtable_install_test bigtable::client)

add_executable(storage_install_test ../storage_install_test.cc)
target_link_libraries(storage_install_test storage_client)
