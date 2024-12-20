## Beispiel 
- code 
	```python
	# define cnn model
	def define_model():
	    model = keras.models.Sequential()
	    model.add(keras.layers.Resizing(227, 227, interpolation="bilinear", crop_to_aspect_ratio=False))
	    model.add(keras.layers.Conv2D(filters=96, kernel_size=(11,11), strides=(4,4), activation='relu', input_shape=(227,227,3)))
	    model.add(keras.layers.MaxPool2D(pool_size=(3,3), strides=(2,2)))
	    model.add(keras.layers.Conv2D(filters=256, kernel_size=(5,5), strides=(1,1), activation='relu', padding="same"))
	    model.add(keras.layers.MaxPool2D(pool_size=(3,3), strides=(2,2)))
	    model.add(keras.layers.Conv2D(filters=384, kernel_size=(3,3), strides=(1,1), activation='relu', padding="same"))
	    model.add(keras.layers.Conv2D(filters=384, kernel_size=(1,1), strides=(1,1), activation='relu', padding="same"))
	    model.add(keras.layers.Conv2D(filters=256, kernel_size=(1,1), strides=(1,1), activation='relu', padding="same"))
	    model.add(keras.layers.MaxPool2D(pool_size=(3,3), strides=(2,2)))
	    model.add(keras.layers.Flatten())
	    model.add(keras.layers.Dense(4096, activation='relu'))
	    model.add(keras.layers.Dropout(0.5))
	    model.add(keras.layers.Dense(4096, activation='relu'))
	    model.add(keras.layers.Dropout(0.5))
	    model.add(keras.layers.Dense(10, activation='softmax'))
	    # compile model
	    opt = keras.optimizers.SGD(learning_rate=0.001, momentum=0.9)
	    model.compile(optimizer=opt, loss='sparse_categorical_crossentropy', metrics=['accuracy'])
	
	    model.build(input_shape=(None, 227,227,3)) # `input_shape` is the shape of the input data, e.g. input_shape = (None, 32, 32, 3)
	    #summary of the model
	    #Can you calculate the number of parameters for each layer?
	    #How many parameters has the first convolutional layer?
	    #Answer: 34944 = 11 * 11 * 3 * 96 + 96
	    model.summary()
	    return model
	
	# entry point, run the test harness
	history, model = run_test_harness()
	```
- Ergebnis: ![|625](https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-01_16-27-03.png?raw=)
- Rechenbeispiel 
	- Conv-Layer 1 
		- Ausgabegröße 
			- Eingabe 227 x 227 $\rightarrow$ n = 227 
			- no Padding $\rightarrow$ p = 0
			- Filter: 11 x 11 $\rightarrow$ f = 11 
			- Stride s = 4 
			- $\Rightarrow$ (227 - 11) / 4 + 1 = 55 
			- Anzahl der Filter = 96 $\Rightarrow$ Ausgabeklasse = 96 
			- $\Longrightarrow$ 55 x 55 x 96 
		- Anzahl der Parameter 
			- Filter 11 x 11 
			- Kanäle in Eingabe 3 
			- Anzahl der Filter 96 
			- $\Longrightarrow$ 96 x (11 x 11 x 3 + 1) = 34944 
		- Speicherbedarf 
			- Batch Size 16 
			- Präzision KB 
			- $\Longrightarrow$ 16 x 34944 / (8 x 1000) = 69.888 KB 

