cmake_minimum_required(VERSION 3.5)
project(put_husky_description)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
##### ADD #####
find_package(urdf REQUIRED)
### END ADD ###


##### ADD #####
install(DIRECTORY launch meshes urdf
  DESTINATION share/${PROJECT_NAME}
)
### END ADD ###

##### ADD #####
ament_export_dependencies(xacro)
ament_export_dependencies(urdf)
### END ADD ###
ament_package()