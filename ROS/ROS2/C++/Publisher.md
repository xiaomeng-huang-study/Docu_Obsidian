- Kopf
```c++
#include <rclcpp/rclcpp.hpp>
```
- Klasse
```c++
class Publisher : public rclcpp::Node
{
	public:
		Publisher():Node("${NODE_NAME}")
		{
			pub = this->create_publisher<${MESSAGE_TYP}>("${TOPIC_NAME}", 10);

			time_period = std::chrono::milliseconds(100)
			timer = this->create_timer(time_period, std::bind(&Publisher::timer_callback, this));
		}
	private:
		void timer_callback()
		{
			...
		}
		rclcpp::Publisher<${MESSAGE_TYP}>::SharedPtr pub;
		rclcpp::TimerBase::SharedPtr timer;
}
```
- main
```c++
int main(int argc, char * argv[])
{
	rclcpp::init(argc, argv);
	while(rclcpp::ok())
	{
		rclcpp::spin(std::make_shared<Publisher>());
		...
	}
	rclcpp::shutdown();
	return 0
}
```