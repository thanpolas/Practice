# Advanced Git Cheatsheet

## Remove folder from repo with history

```shell
git filter-branch -f --tree-filter 'rm -rf folder/path' HEAD
```

[source blog post](http://dalibornasevic.com/posts/2-permanently-remove-files-and-folders-from-a-git-repository), [Stack Overflow](http://stackoverflow.com/questions/10067848/remove-folder-and-its-contents-from-git-githubs-history), [git-scm](http://git-scm.com/book/en/Git-Internals-Maintenance-and-Data-Recovery)

## Move a folder to another repository

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
