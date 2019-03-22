# Git-Flow
----------

## Definitions

- ***master branch***
represents the latest production release, tagged with a version.
- ***develop branch***
represents the latest delivered development changes for the next release. Initially derived from master, then merged with the features content.
When develop content is ready to be released, all of the changes are merged back into master and then tagged with a release version.
- ***feature branch***
represents a new feature development (a use-case or his sub-part). Is derived from develop, when finished is merged back into develop, and then removed.
- ***release branch***
represent the "release candidate" to test and then deploy as production release.
Is derived from develop, and after tests (QA, UAT) and version bump, the release is merged back into develop and master, and then removed.
Merge on master creates a new version tag (x.y.0).
- ***hotfix branch***
represent the solution to an opened production issue. After the solution the hotfix is merged into master and develop. Merge on master creates a new version tag (x.y.<hotfix_number>).


## Operations

### Create remote repository "*origin*"

On remote host:

	cd <git-repos-url>
	git init --bare <repo-name>.git


### Clone repository on client host

On client host:

	cd <git-repos-url>
	git clone <remote-url>/<repo-name>.git
	cd <git-repos-url>
	git flow init -d
	git config --local user.name <name>
	git config --local user.email <email>


### Create, work and publish a *feature*

update local branch *develop*:

    git checkout develop
	git pull origin develop

create the *feature* based on current *develop*:

	git flow feature start <feature>

work and publish the *feature*:

	git status... git add... git commit...
	git flow feature publish <feature>


### Work with existents *feature*

update local branch *feature*:

	git flow feature track <feature>
	git pull origin <feature>

work and publish the *feature*:

	git status... git add... git commit...
	git flow feature publish <feature>

finish the *feature*:

	git flow feature finish
	git push origin


### Create, work and publish a *release*

update local branch *develop*:

    git checkout develop
	git pull origin develop

create the *release* based on current *develop*:

	git flow release start <x.y.0>

work and publish the *release*:

	git status... git add... git commit...
	git flow release publish <x.y.0>


### Work with existents *release*

update local branch *release*:

	git flow release track <x.y.0>
	git pull origin <x.y.0>

work and publish the *release*:

	git status... git add... git commit...
	git flow release publish <x.y.0>

finish the *release*:

	git flow release finish <x.y.0>
	git push origin develop master
	git push origin --tags


### Work with a *hotfix*

update local branch *develop*:

    git checkout develop
	git pull origin develop

create, work and finish the *hotfix*:

	git flow hotfix start <x.y.z>
	git status... git add... git commit...
	git flow hotfix finish [x.y.z]
	git push origin develop master
	git push origin --tags


## Usefull Commands

	git remote [-v]
	git status [-s]
	git branch [-v]
	git flow feature list
	git flow feature diff
	git flow release list
	git flow hotfix list

	git push origin --delete <branch-name>

	set | grep -i ssh
	ssh -l username -p port hostname
	cat ~/.ssh/id_rsa.pub | ssh -l username -p port hostname keys add


## References
* [Getting Started - Git](https://yakiloo.com/getting-started-git/)
* [Getting Started - Git-Flow](/https://yakiloo.com/getting-started-git-flow/)
* [Using git-flow to automate your git branching workflow](http://jeffkreeftmeijer.com/2010/why-arent-you-using-git-flow/)
* [Learn Git](https://www.atlassian.com/git/tutorials/learn-git-with-bitbucket-cloud)
* [Gitflow CLA](https://github.com/nvie/gitflow/wiki/Command-Line-Arguments)