# CMake instructions to make the static lib

ADD_LIBRARY( libfmsynth STATIC
             src/fmsynth.c )

target_include_directories( libfmsynth PUBLIC include )
