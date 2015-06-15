cmake_minimum_required (VERSION 3.0.2)
project (matplotpp)

find_package(GLUT REQUIRED)
find_package(OpenGL REQUIRED)

include_directories(${GLUT_INCLUDE_DIR})

set(BUILD_EXAMPLES ON CACHE BOOL "Build examples")

add_library(matplotpp gl2ps.c matplotpp.cc)

if(${BUILD_EXAMPLES})
include_directories(${PROJECT_BINARY_DIR})
link_directories(${PROJECT_BINARY_DIR})
SET (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/examples )

add_executable(ex101_creating_a_plot examples/ex101_creating_a_plot.cc)
target_link_libraries(ex101_creating_a_plot matplotpp ${OPENGL_LIBRARIES} ${GLUT_LIBRARIES})
add_executable(ex102_mouse_and_keyboard_events examples/ex102_mouse_and_keyboard_events.cc)
target_link_libraries(ex102_mouse_and_keyboard_events matplotpp ${OPENGL_LIBRARIES} ${GLUT_LIBRARIES})
add_executable(ex103_multiple_plots examples/ex103_multiple_plots.cc)
target_link_libraries(ex103_multiple_plots matplotpp ${OPENGL_LIBRARIES} ${GLUT_LIBRARIES})
add_executable(ex104_style_and_color examples/ex104_style_and_color.cc)
target_link_libraries(ex104_style_and_color matplotpp ${OPENGL_LIBRARIES} ${GLUT_LIBRARIES})
add_executable(ex105_axes examples/ex105_axes.cc)
target_link_libraries(ex105_axes matplotpp ${OPENGL_LIBRARIES} ${GLUT_LIBRARIES})
add_executable(ex106_surface_and_contour examples/ex106_surface_and_contour.cc)
target_link_libraries(ex106_surface_and_contour matplotpp ${OPENGL_LIBRARIES} ${GLUT_LIBRARIES})
add_executable(ex107_3d_line_and_surface examples/ex107_3d_line_and_surface.cc)
target_link_libraries(ex107_3d_line_and_surface matplotpp ${OPENGL_LIBRARIES} ${GLUT_LIBRARIES})
add_executable(ex108_animation examples/ex108_animation.cc)
target_link_libraries(ex108_animation matplotpp ${OPENGL_LIBRARIES} ${GLUT_LIBRARIES})
endif(${BUILD_EXAMPLES})