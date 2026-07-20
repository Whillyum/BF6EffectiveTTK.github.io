cmake_minimum_required(VERSION 3.28)
project(BF6TTK)

set(CMAKE_CXX_STANDARD 26)

add_executable(BF6TTK main.cpp
        Weapon.cpp
        Weapon.h
        Attachment.cpp
        Attachment.h
)

if (EMSCIPTEN)
    set_target_properties(BF6TTK PROPERTIES OUTPUT_NAME "index")
    set_target_properties(BF6TTK PROPERTIES SUFFIX ".html")

    target_link_options(BF6TTK PRIVATE
        "-sWASMEDGE=0"
        "-sEXPORTED_FUNCTIONS=['_main','_add']" # Replace/add your exported C functions
        "-sEXPORTED_RUNTIME_METHODS=['ccall','cwrap']"
        "-sALLOW_MEMORY_GROWTH=1"
    )
endif()