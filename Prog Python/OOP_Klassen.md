- Klasse definieren 
	```python
	class Class_Name:
		...
	```
	- Class_Name
		- Pascal
			- Beispiel
				- `UserAccount` 
				- `CustomerOrder` 
				- `PaymentData` 

- Konstruktion
	- Konstruktor 
		```python
		def __init__(self, para1):
			self.m_Variable1 = para1
			...
		```
	- in Aufrufer 
		```python
		ob1 = Class_Name(Para1)
		```

- Memberfunktionen
	```python
	def func01(self, para1):
		...
	```
	- in Aufrufer 
		```python
		ob1.func01(Para1)
		```

- Beispiel 
	```python
	class Student:
	    def __init__(self, name, student_id):
	        self.Name = name
	        self.Student_Id = student_id
	        self.Noten = {"Fach1": 0, "Fach2": 0, "Fach3": 0}
	
	    def aendernNoten(self, fach, note):
	        if fach in self.Noten.keys():
	            self.Noten[fach] = note
	        else:
	            print(f"{fach} nicht vorhanden")
	
	    def zeigenNoten(self):
	        print(f"Name: {self.Name}, ID: {self.Student_Id}")
	        for temp_fach, temp_note in self.Noten.items():
	            print(f"{temp_fach}: {temp_note}")
	
	
	Student1 = Student("Name_Student1", "Id_Student1")
	Student1.zeigenNoten()
	Student1.aendernNoten("Fach1", 60)
	Student1.zeigenNoten()
	Student1.aendernNoten("Fach4", 60)
	Student1.zeigenNoten()
	```

