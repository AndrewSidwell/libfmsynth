# CMake instructions to make the static lib

ADD_LIBRARY( libfmsynth STATIC
             src/fmsynth.c )

target_include_directories( libfmsynth PUBLIC include )

if(MSVC)
    set_property(TARGET libfmsynth PROPERTY
        MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
    target_compile_options(libfmsynth INTERFACE /arch:AVX)
else()
    target_compile_options(libfmsynth INTERFACE -mavx)
endif()

target_compile_definitions(libfmsynth PRIVATE FMSYNTH_SIMD)
