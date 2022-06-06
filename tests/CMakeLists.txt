cmake_minimum_required(VERSION 3.1)

find_package(GTest REQUIRED)
include_directories(${gtest_SOURCE_DIR}/include ${gtest_SOURCE_DIR})

set(test_dirs
	ballistics
	pbr
)

set(test_sources)
foreach (example_dir ${example_dirs})
    file(GLOB sources ${example_dir}/*.c)
    list(APPEND test_sources ${sources})
endforeach ()

add_executable(runTests ${test_sources})

target_link_libraries(runTests gtest gtest_main pthread)
target_link_libraries(runTests ballistics)