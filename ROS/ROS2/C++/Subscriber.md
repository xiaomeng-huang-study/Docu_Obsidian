- Kopf
```c++
#include <rclcpp/rclcpp.hpp>
```
- Klasse
```c++
class Subscriber : public rclcpp::Node
{
	public:
		Subscriber():Node("${NODE_NAME}")
		{
			sub = this->create_subscription<${MESSAGE_TYP}>("${TOPIC_NAME}", 10, std::bind(&Subscriber::callback_func, this, std::placeholders::_1));
		}
	private:
		void callback_func(${MESSAGE_TYP} _msg)
		{
			...
		}

		rclcpp::Subscription<${MESSAGE_TYP}>::SharedPtr sub;
}
```
- main
```c++
int main(int argc, char * argv[])
{
	rclcpp::init(argc, argv);
	while(rclcpp::ok())
	{
		rclcpp::spin(std::make_shared<Subscriber>());
		...
	}
	rclcpp::shutdown();
	return 0
}
```