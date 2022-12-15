## git remote 
### 1) add 
#### **`git remote add <URL_Abkürzung> <URL>`**
- URL_Abkürzung : origin
- URL: https://...
- Funktion: Zugang zu einem Server 
- Beispiel: ==git remote add origin https://... ==
- ![](https://raw.githubusercontent.com/ICH-BIN-HXM/images/main/pictures_Obsidian/git_remote_add.png)


## git fetch : <font color="red">master(Server) --> origin/master</font>
#### **`git fetch <URL_Abkürzung>`** 
- Funktion
	- lokaler origin/master wird mit master auf Server synchronisiert 
	- zwi. <u>master(Server)</u> und <u>origin/master</u> 
- Beispiel: ==git fetch origin== 
- ![](https://raw.githubusercontent.com/ICH-BIN-HXM/images/main/pictures_Obsidian/git_fetch.png)


## git push : <font color="red">origin/myBranch --> myBranch(Server)</font>
#### **`git push <origin> <branch_local>: <branch_remote>`** 
- "`:<branch_remote>` "kann weggelassen , wenn die Namen entsprechen 
- Funktion
	- origin/branch_local wird zu branch_remote gepushed
	- zwi. <u>origin/myBranch</u> und <u>myBranch(Server)</u> 
- Beispiel: ==git push origin myBranch== 

## git checkout : <font color="red">origin/myBranch --> myBranch</font>
#### **`git checkout -b <branch_local> <origin>/<branch_local>`** 
- b: new Branch
- Funktion
	- branch_local richtet sich auf origin/branch_local
	- zwi. <u>origin/branch</u> und <u>branch</u> 
- Beispiel: ==git checkout -b myBranch origin/myBranch== 

## git merge 
#### **`git merge <m_branch>`** 
- Funktion: m_branch wird mit aktueller Branch gemerget

## git branch 
#### 1) **`git branch -u <origin>/<branch_local> <branch_local>`** : <font color="red">origin/myBranch --> myBranch</font>
- Funktion
	- branch_local verfolgt origin/branch_local
	- zwi. <u>origin/branch</u> und <u>branch</u> 
- Beispiel: ==git branch -u origin/master master== 
### 2) **`git branch -vv`** 
- ahead: Commits, die noch nicht zum Server gepusht 
- behind: Commits auf dem Server, die noch nicht gemerged
- sonst: up to date
- ![](https://raw.githubusercontent.com/ICH-BIN-HXM/images/main/pictures_Obsidian/git_branch_-vv.png)

## git rebase
[git rebase详解（图解+最简单示例，一次就懂）_风中一匹狼v的博客-CSDN博客_git rebase](https://blog.csdn.net/weixin_42310154/article/details/119004977) 
