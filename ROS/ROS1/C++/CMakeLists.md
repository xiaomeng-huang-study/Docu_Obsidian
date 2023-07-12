```
add_executable(myPackage src/myNode.cpp)

target_link_libraries(myPackage
	${catkin_LIBRARIES}
)
```