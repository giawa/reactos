
list(APPEND SOURCE
    hhpcomp.cpp
    hhp_reader.cpp
    utils.cpp
    chmc/chmc.c
    chmc/err.c
    lzx_compress/lz_nonslide.c
    lzx_compress/lzx_layer.c
    ../port/mkstemps.c)

# used by lzx_compress
add_definitions(-DNONSLIDE)

add_executable(hhpcomp ${SOURCE})
target_link_libraries(hhpcomp)

if(MSVC)
    # Disable warning "'x': unreferenced local variable"
    target_compile_options(hhpcomp PRIVATE "/wd4101")

    # Disable warning "'=': conversion from 'a' to 'b', possible loss of data"
    target_compile_options(hhpcomp PRIVATE "/wd4244")
endif()
