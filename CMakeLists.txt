cmake_minimum_required(VERSION 3.14)
project(llm-guard CXX)
set(CMAKE_CXX_STANDARD 17)

foreach(EXAMPLE scrub_pii injection_detection guard_pipeline api_key_leak)
    add_executable(${EXAMPLE} examples/${EXAMPLE}.cpp)
    target_include_directories(${EXAMPLE} PRIVATE include)
    target_compile_options(${EXAMPLE} PRIVATE
        $<$<CXX_COMPILER_ID:MSVC>:/W4>
        $<$<NOT:$<CXX_COMPILER_ID:MSVC>>:-Wall -Wextra>
    )
endforeach()
