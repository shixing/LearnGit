LearnGit
========

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

#### Reset/ Checkout / Revert

* git reset is to set the pointer HEAD:

```
git log --oneline

a09a03f V0.1.5
2805f3f V0.1.4

git reset 2805 # this would set HEAD pointing to V0.1.4, but the codes won't change
git checkout -f HEAD # change the code to V0.1.4
or git checkout -- <file>

# Above two commands are equal to the following:

git reset --hard 2805 # This would change HEAD to V0.1.4 and also change the code
```

* git revert 

```
git log --oneline

a09a03f V0.1.5
2805f3f V0.1.4

git revert 2805 # This means merge 2805's code with HEAD's code and commit it, usually cause conflicts.
```

* clean the untracked files and directories.

```
git clean -d -n\-f
```
option -d means directory. -n will print which file would delete. -f will delete them.

#### Branch

* create a new branch:

```
git branch <new_branch>
or
git checkout -b <new_branch>
>>>>>>> feature_branch
```

* merge with master:

```
git checkout master
git merge <new_branch> 
```

* delete branch:

```
git branch -d <new_branch>
```

* tracking remote branch

```
git checkout --track origin/remote_branch
```

* create a branch remotely

```
# create a new branch locally
git branch name_of_branch
git checkout name_of_branch
# edit/add/remove files    
# ... 
# Commit your changes locally
git add fileName
git commit -m Message
# push changes and new branch to remote repository:
git push origin name_of_branch:name_of_branch
```

### Which kind of commit is counted in contributions?

# If you create a new branch and commit changes to this branch, those commits won't be counted!



#### Some notation

* HEAD: the current branch
* HEAD^: previous commit of current branch
* HEAD~n: previous n commit of current branch

#### Reference

http://stackoverflow.com/questions/315911/git-for-beginners-the-definitive-practical-guide/1350157#1350157

