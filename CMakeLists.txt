cmake_minimum_required(VERSION 3.8)
project(my_msgs)

# If desired, add compiler warnings for C++
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# 1) find dependencies
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)   # Needed for generating .msg code
find_package(std_msgs REQUIRED)                    # If your .msg depends on std_msgs

# 2) generate interfaces
#    List all .msg files below inside msg/ folder. For example:
rosidl_generate_interfaces(${PROJECT_NAME}
  msg/Float32MultiArrayStamped.msg
  # Add more .msg files here if you have them
  DEPENDENCIES std_msgs
)

# 3) testing / linting (optional)
if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # skip certain linters if desired
  set(ament_cmake_cpplint_FOUND TRUE)
  set(ament_cmake_copyright_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

# 4) finalize
ament_package()

