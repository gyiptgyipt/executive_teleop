cmake_minimum_required(VERSION 3.8)
project(executive_teleop)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(tf2_ros REQUIRED)
find_package(ff_msgs REQUIRED)
find_package(ff_util REQUIRED)
find_package(ff_common REQUIRED)
find_package(gflags REQUIRED)


if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()


add_executable(teleop_tool src/teleop_tool.cc)
ament_target_dependencies(teleop_tool rclcpp tf2_ros ff_msgs ff_util ff_common gflags)

install(TARGETS
  teleop_tool
  DESTINATION lib/${PROJECT_NAME})

ament_package()
