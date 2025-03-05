# Git Exercises 
## Part 1
### Getting Started:

```bash
PS C:\Users\pc\Documents\Advanced> git init                 
Initialized empty Git repository in C:/Users/pc/Documents/Advanced/.git/
PS C:\Users\pc\Documents\Advanced> git add README.md
PS C:\Users\pc\Documents\Advanced> git commit -m "first commit"
[master (root-commit) 693b72c] first commit
 1 file changed, 7 insertions(+)
 create mode 100644 README.md
PS C:\Users\pc\Documents\Advanced> git branch -M main
PS C:\Users\pc\Documents\Advanced> git remote add origin https://github.com/Tracy120/git.git
PS C:\Users\pc\Documents\Advanced> git push -u origin main
>> 
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 264 bytes | 132.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Tracy120/git.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ touch test{1..4}.md
git add test1.md && git commit -m "chore: Create initial file"
git add test2.md && git commit -m "chore: Create another file"
git add test3.md && git commit -m "chore: Create third and fourth files"
[main 56d2b59] chore: Create initial file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
[main 368ca36] chore: Create another file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
[main 3bd346f] chore: Create third and fourth files
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
```