cmake_minimum_required (VERSION 3.11)

add_library(sisl_version OBJECT)
target_sources(sisl_version PRIVATE
    version.cpp
  )
target_link_libraries(sisl_version ${COMMON_DEPS} zmarok-semver::zmarok-semver)

add_executable(test_version)
target_sources(test_version PRIVATE
    tests/test_version.cpp
  )
target_link_libraries(test_version sisl ${COMMON_DEPS} zmarok-semver::zmarok-semver GTest::gtest)
add_test(NAME Version COMMAND test_version)
