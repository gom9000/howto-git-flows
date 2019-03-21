# Git *master/features* flow
----------------------------

## Definitions

- ***master branch***
represents the latest production release.
- ***feature branch***
represents a new feature development (a use-case or his sub-part). Is derived from master, when finished is merged back into master and then removed.


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


### Add some *templates* to repository

	git add LICENSE
	git add README.md
	git add .gitignore
	git commit -m "Add LICENSE, README and .gitignore"

### Add new *feature* and publish it on remote repository

update local branch *master*:

    git checkout master
	git pull origin master

create and publish new branch *feature* based on current *master*:

	git branch <feature>				
	git push -u origin <feature>


### Work with *feature* branch

update local branch *feature*:

	git chechout -b <feature>
	git pull origin <feature>

add stuff to *feature* and publish it:

	git status
	git add <some-files>
	git commit -m "<commit-message>"
	git push -u origin <feature>


### Release the completed *feature* on master and remove it

update local branches *master* and *feature*:

	git checkout master
	git pull origin master
	git checkout <feature>
	git pull origin <feature>

merge *feature* into *master*:

	git rebase -i master
	git checkout master
	git merge --no-ff <feature>
	git push -u origin master

clean local and remote branch *feature*:

	git push origin --delete <feature>
	git branch -d <feature>


### Tag *master* with release *version*

update local branches *master*:

	git checkout master
	git pull origin master

tag *master* with release *version*:

	git tag <version>
	git push origin --tags
