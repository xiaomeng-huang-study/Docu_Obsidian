```txt
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(${MESSAGE_TYPE} REQUIRED)
```

```
add_executable(${PACKAGE_NAME} src/my_node.cpp)
ament_target_dependencies(
  ${PACKAGE_NAME}
  rclcpp

)
```

```txt
install(TARGETS
    my_node
    DESTINATION lib/${PROJECT_NAME})
```