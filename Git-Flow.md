# Git Flow

## General

* For remote names use `origin` and `upstream` where it applies.

## Flow Overview

Following the [Github Flow][] paradigm, in short:

* Each developer creates a new branch out of master or target branch.
* Works on the branch doing [Atomic Commits](http://en.wikipedia.org/wiki/Atomic_commit)
* Pushes to *origin* often
* When done performs a **Pull Request** to master or the target branch.

### DO NOT

* DO NOT Squash your commits

## Keeping up with master

To keep up with the master or your target branch use `rebase`:

```
git rebase upstream/master
```

### Resolving Conflicts with rebase

When a conflict occures from rebase it will halt the operation and wait for you to resolve the conflicts. Once all conflicts are resolved use the following command sequence to resume rebasing:

```shell
git add .
git rebase --continue
```

## More Reading

* [Github Flow][]
* [Rolling back changes with revert](http://gitready.com/intermediate/2009/03/16/rolling-back-changes-with-revert.html)
* [Gitmagic Git Complete Reference](http://www-cs-students.stanford.edu/~blynn/gitmagic/)

[Github Flow]: http://scottchacon.com/2011/08/31/github-flow.html
