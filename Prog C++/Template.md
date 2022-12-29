- Function Template
	```c++
	template<typename T>
	void func(T pa, T pb)
	{
		...
	}
	```

	```c++
	func<int>(a, b);
	```

- Class Template
	- in .tpp (<font color = "red">alles in .h implementieren</font>)
		```c++
		template<class T1, class T2>
		class classA
		{
		public:
			void func(T1 pa, T2 pb);
		protected:
		private:
			T1 a;
			T2 b
		};
		
		template<class T1, class T2>
		void classA<T1,T2> ::func(T1 pa, T2 pb)
		{
		
		}
		```
	- Instanzierung
		```c++
		classA<int,int> ob1(10,20);
		```