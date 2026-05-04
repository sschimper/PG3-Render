cmake_minimum_required(VERSION 3.14)
project(PG3Render)
set(CMAKE_CXX_STANDARD 14)

# macOS / AppleClang needs libomp installed via Homebrew
if(APPLE)
    # Tell CMake where Homebrew's libomp lives
    set(OpenMP_C_FLAGS "-Xpreprocessor -fopenmp")
    set(OpenMP_CXX_FLAGS "-Xpreprocessor -fopenmp")
    set(OpenMP_C_LIB_NAMES "omp")
    set(OpenMP_CXX_LIB_NAMES "omp")
    set(OpenMP_omp_LIBRARY "/opt/homebrew/opt/libomp/lib/libomp.dylib")
    include_directories("/opt/homebrew/opt/libomp/include")
endif()

find_package(OpenMP REQUIRED)

include_directories(src)

add_executable(PG3Render
    src/camera.hxx
    src/config.hxx
    src/directillum.hxx
    src/eyelight.hxx
    src/framebuffer.hxx
    src/geometry.hxx
    src/lights.hxx
    src/materials.hxx
    src/math.hxx
    src/pathtracer.hxx
    src/pg3render.cxx
    src/ray.hxx
    src/renderer.hxx
    src/rng.hxx
    src/scene.hxx
    src/utils.hxx)

target_link_libraries(PG3Render PRIVATE OpenMP::OpenMP_CXX)