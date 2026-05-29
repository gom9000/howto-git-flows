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
