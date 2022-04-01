# Git *master/feature* flow
----------------------------

## Definitions

- ***master branch***
represents the latest production release.
- ***feature branch***
represents a new feature development (a use-case or his sub-part). Is derived from master, when finished is merged back into master and then removed.


## Operations

### Add new *feature* and, if needed, publish it on remote repository

update local branch *master*:

    git checkout master
	git pull origin master

create new branch *feature* based on current *master*:

	git branch <feature>
    git checkout <feature>
 
 or with a single command:

	git chechout -b <feature> master

publish new branch *feature* on remote repository (origin):

	git push origin <feature>


### Work with *feature* branch

update, if previously published, local branch *feature*:

	git chechout <feature>
	git pull origin <feature>

add stuff to *feature* and, if needed, publish it:

	git status
	git add <some-files>
	git commit -m "<commit-message>"
	git push origin <feature>


### Release the completed *feature* on master and remove it

update local branch *master* and update, if previously published, local branch *feature*:

	git checkout master
	git pull origin master
	git checkout <feature>
	git pull origin <feature>

rebase, if needed, the *feature* commits to produce a clean history:

    git rebase -i <commit-hash>

rebase the *feature* on latest commits on master to maintain a linear history:

    git rebase master

merge *feature* into *master*, if possible without merge commit:

	git checkout master
	git merge <feature>
	git push origin master

or merge *feature* into *master*, with merge commit:

	git checkout master
	git merge --no-ff <feature>
	git push origin master

clean local and remote branch *feature*:

	git branch -d <feature>
	git push origin --delete <feature>


### Tag *master* with release *version* and publish it on remote repository

update local branches *master*:

	git checkout master
	git pull origin master

tag *master* with release *version*:

	git tag <version>
	git push origin --tags
