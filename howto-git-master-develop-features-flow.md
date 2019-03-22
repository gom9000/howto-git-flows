# Git *master/develop/features* flow
------------------------------------

## Definitions

- ***master branch***
represents the latest production release, tagged with a version.
- ***develop branch***
represents the latest delivered development changes for the next release. Initially derived from master, then merged with the features content.
When develop content is ready to be released, all of the changes are merged back into master and then tagged with a release version.
- ***feature branch***
represents a new feature development (a use-case or his sub-part). Is derived from develop, when finished is merged back into develop and then removed.


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


### Add *develop* branch and publish it on remote repository

	git branch develop
	git push -u origin develop


### Add new *feature* and publish it on remote repository

update local branch *develop*:

    git checkout -b develop
	git pull origin develop

create and publish new branch *feature* based on current *develop*:

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


### Release the completed *feature* on develop and remove it

update local branches *develop* and *feature*:

	git checkout develop
	git pull origin develop
	git checkout <feature>
	git pull origin <feature>

merge *feature* into *develop*:

	git rebase -i develop
	git checkout develop
	git merge --no-ff <feature>
	git push -u origin develop

clean local and remote branch *feature*:

	git push origin --delete <feature>
	git branch -d <feature>


### Release *develop* on *master* and tag *master* with release *version*

update local branches *master* and *develop*:

	git checkout master
	git pull origin master
	git checkout develop
	git pull origin develop

merge *develop* into *master*:

	git checkout master
	git merge develop
	git push -u origin master

tag *master* with release *version*:

	git tag <version>
	git push origin --tags
