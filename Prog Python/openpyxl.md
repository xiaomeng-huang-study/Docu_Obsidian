- new Workbook 
	```python
	from openpyxl import Workbook
	wb = Workbook()
	```
- load workbook 
	```python
	from openpyxl import load_workbook
	wb = load_workbook(r"...")
	```
- worksheet 
	```python
	ws = wb.active
	```
	```python
	ws = wb["Sheet1"]
	```
- save 
	```python
	wb.save(r"...")
	```
