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
  * If an issue exists (like in most cases) then they are expected to attach the Pull Request onto that issue using [HUB][], [here's how to do it](#working-with-hub).

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

## Working with hub

Install Github's command line utility [`hub`][hub]:

#### On OSX:

```shell
$ brew install hub
```

#### From source:

```shell
$ git clone https://github.com/github/hub.git
$ cd hub
$ rake install prefix=/usr/local
```

### Authorize hub

You need to authorize hub with your Github account using an oAuth token, [follow the instructions illustrated in this comment to create the token and provide it to `hub`](https://github.com/github/hub/issues/491#issuecomment-35631300)

### Attaching Pull Requests to existing issues

To attach a PR to an existing issue use the following command:

#### When you work on a Fork

```shell
$ hub pull-request -b USERNAME_OF_UPSTREAM_OWNER:UPSTREAM_BRANCH -h YOUR_USERNAME:YOUR_BRANCH URL_TO_ISSUE
```

hub pull-request -b thanpolas:master -h thanpolas:csrf https://github.com/thanpolas/check-connectivity/issues/9

#### When you work on the same repository

```shell
hub pull-request -i 4
```

Where `-i 4` is the issue's id.

Source: [Stackoverflow question](http://stackoverflow.com/questions/4528869/how-do-you-attach-a-new-pull-request-to-an-existing-issue-on-github).

## More Reading

* [Github Flow][]
* [Rolling back changes with revert](http://gitready.com/intermediate/2009/03/16/rolling-back-changes-with-revert.html)
* [Gitmagic Git Complete Reference](http://www-cs-students.stanford.edu/~blynn/gitmagic/)

[Github Flow]: http://scottchacon.com/2011/08/31/github-flow.html
[hub]: http://hub.github.com/

