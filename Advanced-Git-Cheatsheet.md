# Advanced Git Cheatsheet

## Remove folder from repo with history

```shell
git filter-branch -f --tree-filter 'rm -rf folder/path' HEAD
```

[blog post](http://dalibornasevic.com/posts/2-permanently-remove-files-and-folders-from-a-git-repository), [Stack Overflow](http://stackoverflow.com/questions/10067848/remove-folder-and-its-contents-from-git-githubs-history), [git-scm](http://git-scm.com/book/en/Git-Internals-Maintenance-and-Data-Recovery)
