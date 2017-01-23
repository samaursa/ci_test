cmake_minimum_required(VERSION 2.8)
project(CI)

include(ExternalProject)

ExternalProject_Add(catch
  GIT_REPOSITORY "https://github.com/samaursa/catch.git" 
  GIT_TAG "master"

  SOURCE_DIR "${CMAKE_SOURCE_DIR}/dep/catch"
  CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${CMAKE_SOURCE_DIR}/install/catch/

  TEST_COMMAND ""
  )

set(CATCH_INCLUDE_DIR "${CMAKE_SOURCE_DIR}/install/catch/include/")

ExternalProject_Add(game
  SOURCE_DIR "${CMAKE_SOURCE_DIR}/game/"

  CMAKE_ARGS -DGAME_SUPERBUILD_DIR=${CMAKE_SOURCE_DIR} -DCMAKE_INSTALL_PREFIX=${CMAKE_SOURCE_DIR}/install/game/

  TEST_COMMAND ""
  )

enable_testing()
#add_test(NAME MathTest COMMAND Test)
