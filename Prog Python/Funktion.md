```python
def func01(para1, para2):
	#Code...
	return ...
```
- Beispiel 
	```python
	def calculate_BMI(weight, height):
	    BMI = weight / (height**2)
	    if BMI <= 18.5:
	        category = "thin"
	    elif 18.5 < BMI <= 25:
	        category = "normal"
	    elif 25 < BMI <= 30:
	        category = "fat"
	    else:
	        category = "very fat"
	    print(f"BMI: {category}")
	    return BMI
	
	BMI = calculate_BMI(72.5, 1.90)
	print(BMI)
	```

