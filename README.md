LearnGit
========

#### git checkout <file>

This would revert the change of <file> to HEAD.

For example, file a.txt:
```
Hello world!
```
You commit it by 'git commit'

Then you change it to:
```
ABC
```
Then you use 
```
git checkout a.txt
```
The file would change to:
```
Hello world!
```

#### git add <file> & git reset HEAD <file>
git add to add <file> into stage ( waiting to commit ). git reset HEAD <file> will remove <file> from stage.

#### Show information

* git status: will show whether there are files not in stage or not committed yet.

* git show <branch/commit>: will show the commit's information, usually includes summary and diff information.

* git log --graph --oneline: will show a brief history of all commits in current branch

* cat .git/HEAD: will show which branch does HEAD refer to.

Another change
 