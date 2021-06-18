cmake_minimum_required(VERSION 3.0.0)

project(vulkan)

set (CMAKE_CXX_STANDARD 20)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/glfw-3.3.4)

add_executable(main main.cpp)

if(DEFINED ENV{VULKAN_SDK})
    set(VULKAN_PATH $ENV{VULKAN_SDK})
else()
    set(VULKAN_PATH C:/VulkanSDK/1.2.176.1)
endif()

target_include_directories(main 
    PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/glfw-3.3.4/include
    PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/glm
    PRIVATE ${VULKAN_PATH}/Include
)


link_directories(${VULKAN_PATH}/Bin;${VULKAN_PATH}/Lib;)

set(VULKAN_LIBRARIES ${VULKAN_PATH}/Lib/vulkan-1.lib)

target_link_libraries(main ${VULKAN_LIBRARIES} glfw ${GLFW_LIBRARIES})
