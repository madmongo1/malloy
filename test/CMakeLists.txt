set(TARGET malloy-tests)

add_executable(${TARGET})

add_subdirectory(test_suites)

target_include_directories(
    ${TARGET}
    PRIVATE
        3rdparty/doctest
)

target_sources(
    ${TARGET}
    PRIVATE
        test_main.cpp
        test.hpp
)

target_link_libraries(
    ${TARGET}
    PRIVATE
        malloy-objs
)

target_compile_options(
    ${TARGET}
    PRIVATE
        -Og
)

###
# CTest
###
enable_testing()

add_test(
    NAME doctest
    COMMAND ${TARGET}
)
