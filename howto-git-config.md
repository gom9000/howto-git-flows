# Git config
------------

## Operations

### Create remote repository

On remote host:

	cd [git-repos-url]
	mkdir <repo-name>.git
	cd <repo-name>.git
	git init --bare


### Clone repository on client host

On client host:

	cd [git-repos-url]
	git clone [remote-url]/<repo-name>.git
	git config --local user.name <name>
	git config --local user.email <email>


### Edit local/global configuration

	git config < --global | --local > --edit


### Edit local/global user data

	git config < --global | --local > user.name <name>
	git config < --global | --local > user.email <email>


### Useful commands

Git:
	git remote [-v]
	git status [-s]
	git branch [-v]
	git push origin --delete [branch-name]


SSH:

	set | grep -i ssh
	cat ~/.ssh/id_rsa.pub | ssh -l username -p port hostname keys add


GitFlow:

	git flow feature list
	git flow feature diff
	git flow release list
	git flow hotfix list