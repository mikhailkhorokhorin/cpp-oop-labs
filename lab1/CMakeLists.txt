cmake_minimum_required(VERSION 3.10.0)
project(CPP-OOP-LABS VERSION 0.1.0 LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)


include_directories(include)

add_executable(lab1
    main.cpp
    src/solution.cpp
)

include(FetchContent)
FetchContent_Declare(
  googletest
  GIT_REPOSITORY https://github.com/google/googletest.git
  GIT_TAG v1.15.0
  TLS_VERIFY false
)
FetchContent_MakeAvailable(googletest)

set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

enable_testing()

add_executable(CPP-OOP-LABS-tests
    tests/tests.cpp
    src/solution.cpp
)

target_link_libraries(CPP-OOP-LABS-tests GTest::gtest_main)

include(GoogleTest)
gtest_discover_tests(CPP-OOP-LABS-tests)

