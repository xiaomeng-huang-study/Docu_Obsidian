- Kopf:
	```python
	import rclpy
	```
- Klasse
	```python
	class Subscriber(Node):
		def __init__(self):
			super().__init__(${NODE_NAME})
			self.subscriber_ = self.create_subscription(${MESSAGE_TYP}, "${TOPIC_NAME}", self.callback_func, 10)
	
		def callback_func(self, _msg):
			pass
			...
	```
- main
	```python
	def main(args = None):
		rclpy.init(args=args)
	
		sub = Subscriber()
	
		rclpy.spin(sub)
		rclpy.shutdown()
	```

```python
if __name__== "__main__":
	main()
```