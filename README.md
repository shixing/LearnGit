LearnGit
========

* git checkout <file>

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