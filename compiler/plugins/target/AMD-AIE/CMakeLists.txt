# Copyright 2023 The IREE Authors
#
# Licensed under the Apache License v2.0 with LLVM Exceptions.
# See https://llvm.org/LICENSE.txt for license information.
# SPDX-License-Identifier: Apache-2.0 WITH LLVM-exception

set(IREE_MLIR_AIR_SOURCE_DIR "${IREE_AMD_AIE_SOURCE_DIR}/third_party/mlir-air/mlir")
set(IREE_PACKAGE_ROOT_DIR "${CMAKE_CURRENT_LIST_DIR}")
set(IREE_PACKAGE_ROOT_PREFIX "iree::target")
set(IREE_COMPILER_TABLEGEN_INCLUDE_DIRS "${CMAKE_CURRENT_SOURCE_DIR}")


add_library(iree_target_amd-aie_compiler_defs INTERFACE)
target_include_directories(iree_target_amd-aie_compiler_defs
  INTERFACE
  ${CMAKE_CURRENT_SOURCE_DIR}
  ${CMAKE_CURRENT_BINARY_DIR}
)

# Configures all iree_cc_* targets to take this implicit dep,
# which provides common includes and copts for the tree.
set(IREE_IMPLICIT_DEFS_CC_DEPS iree_target_amd-aie_compiler_defs)

add_subdirectory(iree-amd-aie)
add_subdirectory(air)
add_subdirectory(Translation)
