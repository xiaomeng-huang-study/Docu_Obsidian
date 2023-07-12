```bash
colcon build --${PARAMETER}
```
- Parameter 
	- --symlink-install 
		- mit Python: nur einmal build, bei weiteren Änderungen ist build nicht erforderlich 
	- --packages-up-to 
		- nur das selektierte Paket und die relevante Pakete werden gebaut. 
	- --packages-ignore 
	- --packages-skip
	- --continue-on-error 