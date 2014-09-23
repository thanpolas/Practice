# Advanced Git Cheatsheet

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

#### When you work on the same repository

```shell
hub pull-request -i 4
```

Where `-i 4` is the issue's id.

Source: [Stackoverflow question](http://stackoverflow.com/questions/4528869/how-do-you-attach-a-new-pull-request-to-an-existing-issue-on-github).


## Remove folder from repo with history

```shell
git filter-branch -f --tree-filter 'rm -rf folder/path' HEAD
```

[source blog post](http://dalibornasevic.com/posts/2-permanently-remove-files-and-folders-from-a-git-repository), [Stack Overflow](http://stackoverflow.com/questions/10067848/remove-folder-and-its-contents-from-git-githubs-history), [git-scm](http://git-scm.com/book/en/Git-Internals-Maintenance-and-Data-Recovery)

### Compact Git Repo

After a `git filter-branch` you run the `git compact` command to remove empty directories from history.

```shell
git gc --aggressive --prune=now
```

Source: [SO Question](http://stackoverflow.com/questions/2116778/reduce-git-repository-size).

## Move a folder to another repository with history

### From Source Repository

```shell
git clone <git repository A url>
cd <git repository A directory>
git remote rm origin
git filter-branch --subdirectory-filter <dir to move> -- --all
mkdir <dir to move>
mv * <dir to move>
git add .
git commit
```

### From Destination Repository

```shell
git clone <git repository B url>
cd <git repository B directory>
git remote add repo-A-branch <git repository A directory>
git pull repo-A-branch master
git remote rm repo-A-branch
```

[source blog post](http://gbayer.com/development/moving-files-from-one-git-repository-to-another-preserving-history/)

[Github Flow]: http://scottchacon.com/2011/08/31/github-flow.html
[hub]: http://hub.github.com/
