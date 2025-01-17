cmake_minimum_required(VERSION 3.17)

# Project
project(
    malloy
    LANGUAGES CXX
    VERSION 0.0.0
)

# Options
option(BUILD_EXAMPLES "Whether to build examples"       ON)
option(BUILD_TESTS    "Whether to build tests"          ON)
option(FEATURE_HTML   "Whether to enable HTML features" ON)
option(FEATURE_TLS    "Whether to enable TLS features"  OFF)

# Set dependencies accordingly
if (FEATURE_TLS)
    set(DEPENDENCY_OPENSSL ON)
endif()

# Add the main library
add_subdirectory(lib)

# Add examples (if supposed to)
if (BUILD_EXAMPLES)
    add_subdirectory(examples)
endif()

# Add tests (if supposed to)
if (BUILD_TESTS)
    add_subdirectory(test)
endif()

# Print options
message("")
message("---------------------")
message("Malloy configuration:")
message("  Build:")
message("    Examples : " ${BUILD_EXAMPLES})
message("    Tests    : " ${BUILD_TESTS})
message("  Features:")
message("    HTML     : " ${FEATURE_HTML})
message("    TLS      : " ${FEATURE_TLS})
message("---------------------")
message("")