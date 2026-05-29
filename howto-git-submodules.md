# Git Submodules
----------------
When the main project depends on other independent Git repositories (e.g. core business logic, or custom frameworks).<br/>
It allows you to embed an entire project inside another while keeping their commit histories separate.


## Definitions

- ***submodule***
is a git repository included inside another git repository. It's a convenient way to manage dependency between repos.


## Operations

### Add submodule to existing repository

	git submodule add <submodule-repo-url>


### Clone a repository and his submodules

	git clone <repo-url> --recursive

    # Initialize submodules if empty after clone
	git submodule update --init --recursive



### Update submodules on a repository

	git submodule update --remote --recursive
