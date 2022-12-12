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
	- ".gitignore" erstellen
	- SSH_pub in Git-Website hinzufügen 
		- kann mit ssh -T git@github.com testen
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
- Repository initializieren
	- cd Repository
	- clonen/ add remote:
		- clonen: `git clone git@...` 
		- remote add: `git remote add origin https://...git` 
		- kann mit `git remote -v` überprüfen
	- `git add .` 
	- `git commit -m 'initialization'` 
	- `git push (-u origin master)` `//u:first time` 
