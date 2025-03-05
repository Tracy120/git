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
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git stash
Saved working directory and index state WIP on main: 4948ab4 ok

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
Dropped refs/stash@{0} (46802a4e829a2860451b5551fbdcf910fa2fadd6)

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git add .
git commit -m "Saving progress before rebase"
[main dbd0d25] Saving progress before rebase
 1 file changed, 5 insertions(+)
# u, update-ref <ref> = track a placeholder for the <ref> to be updated

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git reset --hard
HEAD is now at dbd0d25 Saving progress before rebase

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.

```
## Splitting a Commit:
```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git log --oneline
70924fc (HEAD -> main, origin/main) ok
dbd0d25 Saving progress before rebase
4948ab4 ok
8309950 Save progress before rebase
a56c19f ok
cc2e667 Updated commit to include test4.md
3bd346f chore: Create third and fourth files
368ca36 chore: Create another file
56d2b59 chore: Create initial file
693b72c first commit

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git reset HEAD~1
Unstaged changes after reset:
M       README.md

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git reset
Unstaged changes after reset:
M       README.md

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git add third_file.md
git commit -m "Create Third File"
fatal: pathspec 'third_file.md' did not match any files
On branch main
Your branch is behind 'origin/main' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git add fourth_file.md
git commit -m "Create Fourth File"
fatal: pathspec 'fourth_file.md' did not match any files
On branch main
Your branch is behind 'origin/main' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git log --oneline --graph
* dbd0d25 (HEAD -> main) Saving progress before rebase
* 4948ab4 ok
* 8309950 Save progress before rebase
* a56c19f ok
* cc2e667 Updated commit to include test4.md
* 3bd346f chore: Create third and fourth files
* 368ca36 chore: Create another file
* 56d2b59 chore: Create initial file
* 693b72c first commit

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git push --force
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Tracy120/git.git
 + 70924fc...dbd0d25 main -> main (forced update)
```
## Advanced Squashing:
```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git stash
Saved working directory and index state WIP on main: a81ca9c ok

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
Dropped refs/stash@{0} (563161fef38e37e6383b64012240249e9f2c9eae)

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git add .
git commit -m "Saving progress before rebase"
[main 00d7f66] Saving progress before rebase
 1 file changed, 4 insertions(+)
# u, update-ref <ref> = track a placeholder for the <ref> to be updated

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git reset --hard
HEAD is now at 00d7f66 Saving progress before rebase

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.

```
## Dropping a Commit:
```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git log --oneline
1a7143a (HEAD -> main, origin/main) ok
00d7f66 Saving progress before rebase
a81ca9c ok
dbd0d25 Saving progress before rebase
4948ab4 ok
8309950 Save progress before rebase
a56c19f ok
cc2e667 Updated commit to include test4.md
3bd346f chore: Create third and fourth files
368ca36 chore: Create another file
56d2b59 chore: Create initial file
693b72c first commit

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ touch unwanted.txt
echo "This is an unwanted file" > unwanted.txt
git add unwanted.txt
git commit -m "Unwanted commit"
warning: in the working copy of 'unwanted.txt', LF will be replaced by CRLF the next time Git touches it
[main 3dc98d3] Unwanted commit
 1 file changed, 1 insertion(+)
 create mode 100644 unwanted.txt

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git reset --hard HEAD~1
HEAD is now at 1a7143a ok

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git reset --soft HEAD~1

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git log --oneline
00d7f66 (HEAD -> main) Saving progress before rebase
a81ca9c ok
dbd0d25 Saving progress before rebase
4948ab4 ok
8309950 Save progress before rebase
a56c19f ok
cc2e667 Updated commit to include test4.md
3bd346f chore: Create third and fourth files
368ca36 chore: Create another file
56d2b59 chore: Create initial file
693b72c first commit

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git push --force
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Tracy120/git.git
 + 1a7143a...00d7f66 main -> main (forced update)

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git push --force-with-lease
Everything up-to-date

```
## Reordering Commits:
```bash

```
## Branch Deletion:
```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git branch
  feature-branch
  ft/branch
* main
  new-branch

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git checkout main
Already on 'main'

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git branch
  feature-branch
  ft/branch
* main
  new-branch

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git push origin --delete ft/new-feature
To https://github.com/Tracy120/git.git
 - [deleted]         ft/new-feature

```