cmake_minimum_required(VERSION 3.28)
project(BF6-effective-TTK-sim)

set(CMAKE_CXX_STANDARD 26)

add_executable(BF6-effective-TTK-sim main.cpp
        main.cpp
        Weapon.cpp
        Weapon.h
        Attachment.cpp
        Attachment.h
)

if (EMSCRIPTEN)
    set_target_properties(BF6-effective-TTK-sim PROPERTIES OUTPUT_NAME "index")
    set_target_properties(BF6-effective-TTK-sim PROPERTIES SUFFIX ".html")

    target_link_options(BF6-effective-TTK-sim PRIVATE
        "-sWASMEDGE=0"
        "-sEXPORTED_FUNCTIONS=['_main','_add']" # Replace/add your exported C functions
        "-sEXPORTED_RUNTIME_METHODS=['ccall','cwrap']"
        "-sALLOW_MEMORY_GROWTH=1"
    )
endif()