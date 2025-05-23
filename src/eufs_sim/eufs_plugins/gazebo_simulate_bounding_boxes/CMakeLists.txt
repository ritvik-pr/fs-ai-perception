find_package(ament_cmake REQUIRED)
find_package(tf2_geometry_msgs REQUIRED)  
find_package(tf2_ros REQUIRED)
add_library(gazebo_simulate_bounding_boxes SHARED
  src/gazebo_simulate_bounding_boxes.cpp)

ament_target_dependencies(gazebo_simulate_bounding_boxes
  "gazebo_dev"
  "gazebo_ros"
  "rclcpp"
  "sensor_msgs"
  "eufs_msgs"
  "image_geometry"
  "tf2_ros"
  "tf2_geometry_msgs")

target_include_directories(gazebo_simulate_bounding_boxes PUBLIC include)

ament_export_libraries(gazebo_simulate_bounding_boxes)

install(DIRECTORY config DESTINATION share/${PROJECT_NAME} FILES_MATCHING PATTERN "*.yaml")

install(TARGETS gazebo_simulate_bounding_boxes
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION lib)
