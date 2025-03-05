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
## Missing File Fix:
```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git add test4.md

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git commit --amend -m "Updated commit to include test4.md"
[main cc2e667] Updated commit to include test4.md
 Date: Wed Mar 5 11:31:30 2025 +0200
 2 files changed, 34 insertions(+)
 create mode 100644 test4.md

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git log --oneline -n 1
cc2e667 (HEAD -> main) Updated commit to include test4.md

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git push --force
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 933 bytes | 933.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/Tracy120/git.git
 + 117daae...cc2e667 main -> main (forced update)
```
## Editing Commit History:
```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git stash
Saved working directory and index state WIP on main: a56c19f ok

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git stash pop
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

# u, update-ref <ref> = track a placeholder for the <ref> to be updated
no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (b9634aaae96dc2f4b742e3fa039f81162bac4d59)

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git add .
git commit -m "Save progress before rebase"
[main 8309950] Save progress before rebase
 1 file changed, 5 insertions(+)
# u, update-ref <ref> = track a placeholder for the <ref> to be updated

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git reset --hard
HEAD is now at 8309950 Save progress before rebase

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.

```
## Keeping History Tidy - Squashing Commits:
```bash


```