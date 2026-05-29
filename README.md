# howto-git-flows
A collection of quick notes on the main Git workflows.


## Index

### [master-feature flow](howto-git-master-feature-flow.md)

### [master-develop-feature flow](howto-git-master-develop-feature-flow.md)

### [git-flow](howto-git-flow.md)

### [submodules](howto-git-submodules.md)

## Useful commands
Remove any remote-tracking references that no longer exist on the remote:
```bash
git fetch --prune
```

Create a new local branch from remote \[origin-name\]:
```bash
git checkout --track [origin-name]/[branch-name]
```

Delete a remote \[origin-name\] branch:
```bash
git push [origin-name] --delete [branch-name]
```

Git read status commands:
```
git remote [-v]
git status [-s]
git branch [-v]
```

SSH & Environment:
```bash
	set | grep -i ssh
	cat ~/.ssh/id_rsa.pub | ssh -l username -p port hostname keys add
	ssh -T -p [port] [username]@[hostname]
```
