# Git *master/develop/feature* flow
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

### Add *develop* branch and publish it on remote repository

	git checkout -b develop
	git push -u origin develop


### Add new *feature* and, if needed, publish it on remote repository

update local branch *develop*:

    git checkout develop
	git pull origin develop

create new branch *feature* based on current *develop*:

	git chechout -b <feature> develop

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


### Release the completed *feature* on develop and remove it

update local branch *develop* and update, if previously published, local branch *feature*:

	git checkout develop
	git pull origin develop
	git checkout <feature>
	git pull origin <feature>

merge *feature* into *develop*, if possible without merge commit:

	git checkout develop
	git merge <feature>
	git push origin develop

or merge *feature* into *develop*, with merge commit:

	git checkout develop
	git merge --no-ff <feature>
	git push origin develop

clean local and remote branch *feature*:

	git branch -d <feature>
	git push origin --delete <feature>


### Release *develop* on *master* and tag *master* with release *version*

update local branches *master* and *develop*:

	git checkout master
	git pull origin master
	git checkout develop
	git pull origin develop

merge *develop* into *master*, if possible without merge commit:

	git checkout master
	git merge develop
	git push origin master

or merge *develop* into *master*, with merge commit:

	git checkout master
	git merge --no-ff develop
	git push origin master

tag *master* with release *version*:

	git tag <version>
	git push origin --tags
