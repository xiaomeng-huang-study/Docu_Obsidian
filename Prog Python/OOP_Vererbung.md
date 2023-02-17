- Untere Klassen 
	```python
	class derivedClass_Name(baseClass_Name):
		...
	```
	- Konstruktor 
		- Falls untere Klasse keine eigenen Konstruktor hat 
			- Konstruktor von <font color = "red">oberer</font> Klasse wird aufgerufen 
		- Falls untere Klasse eigenen Konstruktor hat
			- Konstruktor von <font color = "red">unterer</font> Klasse wird aufgerufen 
			- kann Konstruktor von oberer Klasse benutzen 
				- mit `super().__init__(para1, ...)` $\Rightarrow$ Rückgabe: obere Klasse 

- Beispiel 
	```python
	class Employee:
	    def __init__(self, id, name):
	        self.Id = id
	        self.Name = name
	
	    def print_info(self):
	        print(f"ID: {self.Id}, Name: {self.Name}")
	
	
	class FullTimeEmployee(Employee):
	    def __init__(self, id, name, monthly_salary):
	        super().__init__(id, name)
	        self.monthly_Salary = monthly_salary
	
	    def calculate_monthly_pay(self):
	        return self.monthly_Salary
	
	
	class PartTimeEmployee(Employee):
	    def __init__(self, id, name, daily_salary, work_days):
	        super().__init__(id, name)
	        self.daily_Salary = daily_salary
	        self.work_Days = work_days
	
	    def calculate_monthly_pay(self):
	        pay = self.daily_Salary * self.work_Days
	        return pay
	
	
	E1 = FullTimeEmployee("01", "Bob", 1000)
	E2 = PartTimeEmployee("02", "Alice", 30, 20)
	E1.print_info()
	print(f"Employee1: \nPay: {E1.calculate_monthly_pay()}")
	E2.print_info()
	print(f"Employee2: \nPay: {E2.calculate_monthly_pay()}")
	```
