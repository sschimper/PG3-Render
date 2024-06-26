cmake_minimum_required(VERSION 3.0)
project(PG3Render)

set(CMAKE_CXX_STANDARD 14)
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