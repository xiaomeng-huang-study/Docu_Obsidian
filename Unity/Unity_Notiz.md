 - Movement 
	```C#
	//from input to movement vector
	Vector3 movenment = Vector3.right * Input.GetAxis("Horizontal") * moveSpeed * Time.deltaTime;
	transform.Translate(movement);
	
	//creating limits
	Vector3 temp_position = transform.position;
	temp_position.x = Mathf.Clamp(transform.position.x, left_limit, right_limit);
	transform.position = temp_position;
	```

- instantiate 
	```c#
	Instantiate(prefab_object, tranform.position, prefab_object.transform.rotation);
	```

- 

