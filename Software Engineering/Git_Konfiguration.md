- SSH
	- `cd C:\Users\User_Name\.ssh` 
	- `git bash here` 
	- `ssh-keygen -t rsa` : SSH-Schlüssel zu erzeugen
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
		   IdentityFile ~/.ssh/id_rsa_gitlab
		```
	- SSH_pub in Git-Website hinzufügen 
		- kann mit ssh -T git@github.com testen

- Repository initializieren
	- cd Repository
	- `git init` 
	- `touch .gitignore` 
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
	- `git add .`
	- `git commit -m 'initialization'` 
	- `git branch -m Main` 
	- clonen/ add remote:
		- clonen: `git clone git@...` 
		- remote add: `git remote add origin https://...git` 
		- kann mit `git remote -v` überprüfen
	- `git push (-u origin main)` `//u:first time` 

![](https://raw.githubusercontent.com/ICH-BIN-HXM/images/main/pictures_Obsidian/Git_Konfiguration.png)
