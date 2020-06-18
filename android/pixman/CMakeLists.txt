# Sets the minimum version of CMake required to build your native library.
# This ensures that a certain set of CMake features is available to
# your build.

cmake_minimum_required(VERSION 3.4.1)

# Specifies a library name, specifies whether the library is STATIC or
# SHARED, and provides relative paths to the source code. You can
# define multiple libraries by adding multiple add_library() commands,
# and CMake builds them for you. When you build your app, Gradle
# automatically packages shared libraries with your APK.

set(name pixman)

# file(GLOB_RECURSE srcs "../../src/*.cpp")

set(srcs
        ../../pixman/pixman.c
        ../../pixman/pixman-access.c
        ../../pixman/pixman-access-accessors.c
        ../../pixman/pixman-bits-image.c
        ../../pixman/pixman-combine32.c
        ../../pixman/pixman-combine-float.c
        ../../pixman/pixman-conical-gradient.c
        ../../pixman/pixman-filter.c
        ../../pixman/pixman-x86.c
        ../../pixman/pixman-mips.c
        ../../pixman/pixman-arm.c
        ../../pixman/pixman-ppc.c
        ../../pixman/pixman-edge.c
        ../../pixman/pixman-edge-accessors.c
        ../../pixman/pixman-fast-path.c
        ../../pixman/pixman-glyph.c
        ../../pixman/pixman-general.c
        ../../pixman/pixman-gradient-walker.c
        ../../pixman/pixman-image.c
        ../../pixman/pixman-implementation.c
        ../../pixman/pixman-linear-gradient.c
        ../../pixman/pixman-matrix.c
        ../../pixman/pixman-noop.c
        ../../pixman/pixman-radial-gradient.c
        ../../pixman/pixman-region16.c
        ../../pixman/pixman-region32.c
        ../../pixman/pixman-solid-fill.c
        ../../pixman/pixman-timer.c
        ../../pixman/pixman-trap.c
        ../../pixman/pixman-utils.c
    )

include (${ANDROID_GRADLE_NATIVE_BUNDLE_PLUGIN_MK})
include_directories(../../COPKG)

add_library(
        # Specifies the name of the library.
        ${name}

        # Sets the library as a shared library.
        STATIC

        # Provides a relative path to your source file(s).
        ${srcs}
    )

add_definitions(-DPIXMAN_NO_TLS -DHAVE_CONFIG_H)

target_link_libraries(
        ${name}
        android log ${ANDROID_GRADLE_NATIVE_MODULES}
    )
