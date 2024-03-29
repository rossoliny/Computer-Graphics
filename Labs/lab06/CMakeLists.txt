cmake_minimum_required(VERSION 3.10.2)
project(aur)

set(CMAKE_CXX_STANDARD 14)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

include_directories("./include")

set(AUR_SOURCES include/scene/scene.hpp
                include/objects/object.hpp
                include/objects/camera.hpp
                include/objects/mesh.hpp
                include/geometries/vertex.hpp
                include/geometries/geometry.hpp
                include/geometries/es2_geometry.hpp
                include/geometries/geometry_generators.hpp
                include/materials/material.hpp
                include/materials/constant_material.hpp
                include/materials/es2_constant_material.hpp
                include/materials/phong_material.hpp
                include/materials/es2_phong_material.hpp
                include/lights/ambient_light.hpp
                include/lights/light.hpp
                include/lights/directional_light.hpp
                include/lights/point_light.hpp
                include/lights/spot_light.hpp
                include/textures/texture.hpp
                include/textures/es2_texture.hpp
                include/renderer/renderer.hpp
                include/renderer/es2_renderer.hpp
                include/renderer/shader.hpp
                include/renderer/es2_shader.hpp
                include/window/window.hpp
                include/window/sdl_window.hpp
                include/utilities/utilities.hpp
                include/aur.hpp)

add_executable(window_test ${AUR_SOURCES} tests/window_test.cpp)
add_executable(triangle_test ${AUR_SOURCES} tests/triangle_test.cpp)
add_executable(geometry_test ${AUR_SOURCES} tests/geometry_test.cpp)
add_executable(scene_graph_test ${AUR_SOURCES} tests/scene_graph_test.cpp)
add_executable(lightning_test ${AUR_SOURCES} tests/lightning_test.cpp)

target_link_libraries(window_test ${CONAN_LIBS})
target_link_libraries(triangle_test ${CONAN_LIBS})
target_link_libraries(geometry_test ${CONAN_LIBS})
target_link_libraries(scene_graph_test ${CONAN_LIBS})
target_link_libraries(lightning_test ${CONAN_LIBS})
