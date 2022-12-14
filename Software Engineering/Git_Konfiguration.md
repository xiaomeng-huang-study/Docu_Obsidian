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
	- `git init` : .git zu erzeugen
	- (`git branch -m master main` ): master -> main
	- (`touch .gitignore` )
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

- local Repository -> Stage
	- `git add .`
	- `git commit -m 'init'` 
- remote Repository -> Stage
	- `git remote add origin https://...git` (kann mit `git remote -v` überprüfen)
	- `git fetch origin` 
- upstream 
	- `git branch -u origin/main main` : pull durch diese Branch(main)
- `git rebase origin/main main` : die neue Entwicklung von origin/main zu bekommen
- `git push (-u origin main)` //u:first time 

![](https://raw.githubusercontent.com/ICH-BIN-HXM/images/main/pictures_Obsidian/Git_Konfiguration.png)
