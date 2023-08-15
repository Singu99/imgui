# CMakeLists.txt for imgui
cmake_minimum_required(VERSION 3.10)

project(imgui)

# Add the imgui source files
set(IMGUI_SOURCES
    imgui.cpp
    imgui_demo.cpp
    imgui_draw.cpp
    imgui_tables.cpp
    imgui_widgets.cpp
    backends/imgui_impl_glfw.cpp
    backends/imgui_impl_opengl3.cpp
)

# Add the imgui header files
set(IMGUI_HEADERS
    imconfig.h
    imgui.h
    imgui_internal.h
    imstb_rectpack.h
    imstb_textedit.h
    imstb_truetype.h
    backends/imgui_impl_glfw.h
    backends/imgui_impl_opengl3.h
)

# Create the imgui library target
add_library(imgui STATIC ${IMGUI_SOURCES} ${IMGUI_HEADERS})

# Set the include directories for the imgui target
target_include_directories(imgui PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
target_include_directories(imgui PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/backends)

# Set the compile definitions for the imgui target
target_compile_definitions(imgui PUBLIC IMGUI_IMPL_OPENGL_LOADER_GLAD)

# Link the imgui target with glfw and OpenGL libraries
# target_link_libraries(imgui PUBLIC glfw)
# target_link_libraries(imgui PUBLIC OpenGL::GL)
