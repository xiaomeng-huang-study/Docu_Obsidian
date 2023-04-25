- Kopf:
	```python
	import rclpy
	```
- Klasse
	```python
	class Publisher(Node):
		def __init__(self):
			super().__init__(${NODE_NAME})
			self.publisher_ = self.create_subscription(${MESSAGE_TYP}, "${TOPIC_NAME}", 10)

			time_period = 0.5
			self.timer = self.create_timer(time_period, self.timer_callback)
			
		def timer_callback(self):
			msg = ${MESSAGE_TYP}
			...
			self.publisher_.publish(msg)
	```
- main
	```python
	def main(args = None):
		rclpy.init(args=args)
	
		pub = Publisher()
	
		rclpy.spin(pub)
		rclpy.shutdown()
	```

```python
if __name__== "__main__":
	main()
```