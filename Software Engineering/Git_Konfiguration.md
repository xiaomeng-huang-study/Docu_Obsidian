- SSH
	- `cd C:\Users\User_Name\.ssh` 
	- `git bash here` 
	- `ssh-keygen -t rsa` SSH-Schlüssel zu erzeugen
	- `touch config` : config zu erzeugen
		```
		# GITHUB
		Host github.com
		   HostName github.com
		   PreferredAuthentications publickey
		   IdentityFile ~/.ssh/id_rsa_github
		   User ICHBINHXM
		
		# GITLAB
		Host gitlab.com
		   HostName gitlab.com
		   PreferredAuthentications publickey
		   IdentityFile ~/.ssh/id_rsa
		```
	- SSH_pub in Git-Website hinzufügen 
		- kann mit ssh -T git@github.com testen
- Repository initializieren
	- cd Repository 
	- `git add .` 
	- `git commit -m 'first commit'` 
- Konfiguration über User
	- Informationen für alle Repository gültig 
		- `git config --global user.name "..."` 
		- `git config --global user.email "..."`  
	- Informationen nur für diese Repository gültig 
		- `git config user.name "..."` 
		- `git config user.email "..." `
	- get User_name bzw. User_email
		- `git config user.name `
		- `git config user.email` 
- clonen
	- `git clone git@...` 