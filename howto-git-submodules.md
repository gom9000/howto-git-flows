# Git Submodules
----------------

## Definitions

- ***submodule***
is a git repository included inside another git repository. It's a convenient way to manage dependency between repos.


## Operations

### Add submodule to existing repository

	git submodule add <submodule-repo-url>


### Clone a repository and his submodules

	git clone <repo-url> --recursive


### Update submodules on a repository

	git submodule update --remote --recursive
