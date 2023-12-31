cmake_minimum_required(VERSION 3.0)

project(sfml-box2d)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g")

# Set the path to SFML
if(WIN32)
    set(SFML_DIR "<path to sfml>\\lib\\cmake\\SFML")
endif()

# Add the source files to your project
file(GLOB SOURCE_FILES 
    src/*.cpp
)

# Add the executable target
add_executable(${PROJECT_NAME} ${SOURCE_FILES})

# Set the include directories
target_include_directories(${PROJECT_NAME} PUBLIC 
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

# Find SFML package
find_package(SFML 2.5 COMPONENTS system window graphics REQUIRED)

# Link SFML libraries
target_link_libraries(${PROJECT_NAME} PRIVATE
    "${CMAKE_CURRENT_SOURCE_DIR}/external/box2d/lib/libbox2d.a"
    sfml-system 
    sfml-window 
    sfml-graphics
    sfml-audio
)
