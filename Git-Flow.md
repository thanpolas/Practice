# Git Flow

## General

* For remote names use `origin` and `upstream` where it applies.

## Flow Overview

Following the [Github Flow][] paradigm, in short:

* Each developer creates a fork of the repository to their own account.
* Names remotes: their own repository `origin` and the main repository `upstream`.
* Creates a new branch out of `upstream/master` or target upstream branch.
* Works on the branch doing [Atomic Commits](http://en.wikipedia.org/wiki/Atomic_commit).
* Pushes to *origin* often.
* When done performs a **Pull Request** to `upstream/master` or the target branch.
  * If an issue exists (like in most cases) then they are expected to attach the Pull Request onto that issue using [HUB][], [here's how to do it](Advanced-Git-Cheatsheet.md#working-with-hub).

### DO NOT

* [DO NOT Squash your commits](http://thanpol.as/javascript/Dont-Squash-its-rude-and-a-lie/)

## Keeping up with master

To keep up with the master of the original repo use `fetch`:

```
git fetch upstream
```

### How to create the upstream remote

The `upstream` remote refers to the repository that you want to send your Pull Request to. If you have write access on that repository then you don't need it. Otherwise you need to create it:

```
git remote add upstream [uri-of-repository]
```

## Create a new fresh branch

To create a new fresh branch from the original (upstream) master:

```
git checkout upstream/master -b new-local-branch
```

## More Reading

* [Github Flow][]
* [Rolling back changes with revert](http://gitready.com/intermediate/2009/03/16/rolling-back-changes-with-revert.html)
* [Gitmagic Git Complete Reference](http://www-cs-students.stanford.edu/~blynn/gitmagic/)

[Github Flow]: http://scottchacon.com/2011/08/31/github-flow.html
[HUB]: http://hub.github.com/
