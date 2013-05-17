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


#### Pull Branch / Merge / Resolving Merge

First you should know, there are 'local' and 'remote' repos.
```
git log
```
This will show the log info for you current local branch.
```
git log origin
```
This will show the log info for origin (Where to store the remote branches). Usually, 'git log' and 'git log origin' will be the same.

* Fetch objects and refs from remote repo.
```
git fetch
```
This will fetch objects and refs from remote repo to 'origin'.
```
git log origin # this would show the info of remote repo as they are just fetched from remote into origin
git log # show info of local repo, is different from what above shows.
```
However, git fetch won't change your code.

* Merge origin and current branch
```
git merge origin/master
```
This will merge the origin onto your current branch. Your code will be changed. If you use 'git log' and 'git log origin', the outputs are the same.

Or you can use git pull to do a git fetch followed by git merge automatically.

* Resolve the conflicts
If there are conflicts, there would be failed when merging. Also, git will change the conflict files. To resolve the conflicts:
```
vim a.txt # suppose a.txt is conflicted, you should first change a.txt
git add a.txt
git commit # only by committing a.txt, you mark a.txt as resolved
```

#### Switch branches

2nd change
