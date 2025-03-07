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
## Checking Out Detached HEAD:
```bash
$ git add README.md

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (ft/improved-branch-name)
$ git commit -m "Save changes to README.md"
[ft/improved-branch-name 3e1b3c8] Save changes to README.md
 1 file changed, 43 insertions(+)

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (ft/improved-branch-name)
$ git checkout 37463fb
Note: switching to '37463fb'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 37463fb ok

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced ((37463fb...))
$ git stash
No local changes to save

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced ((37463fb...))
$ git checkout 37463fb
HEAD is now at 37463fb ok

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced ((37463fb...))
$ git stash pop
No stash entries found.

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced ((37463fb...))
$ git checkout -- README.md

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced ((37463fb...))
$ git checkout 37463fb
HEAD is now at 37463fb ok


```


### part 3
## Stashing Changes:
```bash

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced ((380de7e...))
$ git status
HEAD detached from 37463fb
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced ((380de7e...))
$ git stash
Saved working directory and index state WIP on (no branch): 380de7e ok

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced ((380de7e...))
$ git stash list
stash@{0}: WIP on (no branch): 380de7e ok

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced ((380de7e...))
$ git stash pop
HEAD detached from 37463fb
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (b74784c4d394885198a2e9da1a3b58d68b42a26a)

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced ((380de7e...))
$ git stash apply
No stash entries found.

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced ((380de7e...))
$
```
## Retrieving Stashed Changes:
```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git checkout main
Already on 'main'
Your branch is up to date with 'origin/main'.

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git stash pop
No stash entries found.

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git add .
git commit -m "Resolved conflicts after stash pop"
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git stash apply
No stash entries found.

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$
```
## Branch Merging Conflicts (Continued):
```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git init merge-conflict-demo
cd merge-conflict-demo
echo "Hello, World!" > conflict.txt
git add .
git commit -m "Initial commit"
Initialized empty Git repository in C:/Users/pc/Documents/Advanced/merge-conflict-demo/.git/
warning: in the working copy of 'conflict.txt', LF will be replaced by CRLF the next time Git touches it
[master (root-commit) 06ba7fc] Initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 conflict.txt

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (master)
$ git checkout -b feature-branch
Switched to a new branch 'feature-branch'

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (feature-branch)
$ echo "This change is from the feature branch." > conflict.txt

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (feature-branch)
$ git add .
git commit -m "Update conflict.txt from feature-branch"
warning: in the working copy of 'conflict.txt', LF will be replaced by CRLF the next time Git touches it
[feature-branch ae43040] Update conflict.txt from feature-branch
 1 file changed, 1 insertion(+), 1 deletion(-)

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (feature-branch)
$ git checkout main
error: pathspec 'main' did not match any file(s) known to git

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (feature-branch)
$ echo "This change is from the main branch." > conflict.txt

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (feature-branch)
$ git add .
git commit -m "Update conflict.txt from main branch"
warning: in the working copy of 'conflict.txt', LF will be replaced by CRLF the next time Git touches it
[feature-branch 3bf4298] Update conflict.txt from main branch
 1 file changed, 1 insertion(+), 1 deletion(-)

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (feature-branch)
$ git merge feature-branch
Already up to date.

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (feature-branch)
$ git add conflict.txt
git commit -m "Resolved merge conflict in conflict.txt"
On branch feature-branch
nothing to commit, working tree clean

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (feature-branch)
$
```
## Retrieving Stashed Changes:

```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git checkout main
Already on 'main'
M       README.md
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$ git stash pop
No stash entries found.

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced (main)
$
```

## Branch Merging Conflicts (Continued):
```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git branch
  feature-branch
* main
  recovery-branch

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git checkout feature-branch
Switched to branch 'feature-branch'

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (feature-branch)
$ git checkout -b feature-branch
fatal: a branch named 'feature-branch' already exists

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (feature-branch)
$ git checkout main
echo "Main branch change" > conflict.txt
git commit -am "Modified conflict.txt on main"
Switched to branch 'main'
warning: in the working copy of 'conflict.txt', LF will be replaced by CRLF the next time Git touches it
On branch main
nothing to commit, working tree clean

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git merge feature-branch
fatal: refusing to merge unrelated histories

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git merge feature-branch --allow-unrelated-histories
warning: in the working copy of 'conflict.txt', LF will be replaced by CRLF the next time Git touches it
error: Your local changes to the following files would be overwritten by merge:
        conflict.txt
Please commit your changes or stash them before you merge.
Aborting
Already up to date.
Merge with strategy ort failed.

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git add conflict.txt
git commit -m "Resolved merge conflict between main and feature-branch"
On branch main
nothing to commit, working tree clean

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git log --oneline --graph --all
* c339642 (HEAD -> main) Modified conflict.txt on main
* 5077efe Modified conflict.txt on feature-branch
* cef0927 Initial commit with conflict.txt
* 0417b78 (origin/main, recovery-branch) Update conflict.txt from feature branch
* 4db5cd7 Update conflict.txt from main branch
* abb748b Initial commit
*   fba1c07 Merge commit 'bf2ea36'
|\
| * bf2ea36 (origin/new-branch-name) ok
| * 380de7e ok

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$
```

## Resolving Merge Conflicts with a Merge Tool:
```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ # Ensure you're in your repository
gi# Ensure you're in your repository
git checkout -b feature-branch conflict.txt
echo "Feature branch change" > conflict.txtature-branch"
git commit -am "Modified conflict.txt on feature-branch"
git checkout main
git checkout main change" > conflict.txt
echo "Main branch change" > conflict.txt main"
git commit -am "Modified conflict.txt on main"
# Attempt to merge (will cause a conflict)
# Attempt to merge (will cause a conflict)
git merge feature-branch
fatal: a branch named 'feature-branch' already exists
warning: in the working copy of 'conflict.txt', LF will be replaced by CRLF the next time Git touches it
[main d6cceb1] Modified conflict.txt on feature-branch
 1 file changed, 1 insertion(+), 1 deletion(-)
Already on 'main'
warning: in the working copy of 'conflict.txt', LF will be replaced by CRLF the next time Git touches it
[main acd9a70] Modified conflict.txt on main
 1 file changed, 1 insertion(+), 1 deletion(-)
fatal: refusing to merge unrelated histories

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git mergetool

This message is displayed because 'merge.tool' is not configured.
See 'git mergetool --tool-help' or 'git help config' for more details.
'git mergetool' will now attempt to use one of the following tools:
opendiff kdiff3 tkdiff xxdiff meld tortoisemerge gvimdiff diffuse diffmerge ecmerge p4merge araxis bc codecompare smerge emerge vimdiff nvimdiff
No files need merging

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git config --global merge.tool meld

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git config --global merge.tool bc3

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git config --global merge.tool kdiff3

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git mergetool
No files need merging

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git add conflict.txt
git commit -m "Resolved merge conflict using git mergetool"
warning: in the working copy of 'conflict.txt', LF will be replaced by CRLF the next time Git touches it
On branch main
nothing to commit, working tree clean

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git log --oneline --graph --all
* acd9a70 (HEAD -> main) Modified conflict.txt on main
* d6cceb1 Modified conflict.txt on feature-branch
* c339642 Modified conflict.txt on main
* 5077efe Modified conflict.txt on feature-branch
* cef0927 Initial commit with conflict.txt
* 0417b78 (origin/main, recovery-branch) Update conflict.txt from feature branch
* 4db5cd7 Update conflict.txt from main branch
* abb748b Initial commit
*   fba1c07 Merge commit 'bf2ea36'
|\

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git config --global mergetool.prompt false

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$

```
## Understanding Detached HEAD State:
```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git checkout HEAD~2  # Checking out a commit two steps before HEAD
Note: switching to 'HEAD~2'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at c339642 Modified conflict.txt on main

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo ((c339642...))
$ git checkout main
Previous HEAD position was c339642 Modified conflict.txt on main
Switched to branch 'main'

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git checkout -b new-branch
Switched to a new branch 'new-branch'

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (new-branch)
$ git checkout main  # Switch back to main branch
git reset --hard HEAD  # Discard changes
Switched to branch 'main'
HEAD is now at acd9a70 Modified conflict.txt on main

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$
```
## Ignoring Files/Directories:
```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ nano .gitignore

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ /tmp
bash: /tmp: Is a directory

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git rm -r --cached tmp
fatal: pathspec 'tmp' did not match any files

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git add .gitignore
git commit -m "Added /tmp to .gitignore to exclude temporary files"
warning: in the working copy of '.gitignore', LF will be replaced by CRLF the next time Git touches it
[main ed95f77] Added /tmp to .gitignore to exclude temporary files
 1 file changed, 10 insertions(+)
 create mode 100644 .gitignore

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git status --ignored
On branch main
nothing to commit, working tree clean

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$
```
## Working with Tags:
```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git push
Everything up-to-date

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git pull
Already up to date.

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git tag v1.0

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git tag
v1.0

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git push origin v1.0
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Tracy120/git.git
 * [new tag]         v1.0 -> v1.0

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git push --tags
Everything up-to-date

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git tag -a v1.0 -m "Version 1.0 release"
git push origin v1.0
fatal: tag 'v1.0' already exists
Everything up-to-date

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git show v1.0
commit ed95f7717170df02e70598b91baba7859b941bf7 (HEAD -> main, tag: v1.0, origin/main)
Author: Tracy Uwase <uwasetracy@120>
Date:   Thu Mar 6 09:49:54 2025 +0200

    Added /tmp to .gitignore to exclude temporary files

diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000..095628d
--- /dev/null

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$
```
## Listing and Deleting Tags:
```bash
pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git tag
v1.0

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git show v1.0  # Shows details about a specific tag
commit ed95f7717170df02e70598b91baba7859b941bf7 (HEAD -> main, tag: v1.0, origin/main)
Author: Tracy Uwase <uwasetracy@120>
Date:   Thu Mar 6 09:49:54 2025 +0200

    Added /tmp to .gitignore to exclude temporary files

diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000..095628d
--- /dev/null

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git tag -d v1.0
Deleted tag 'v1.0' (was ed95f77)

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git push origin --delete v1.0
To https://github.com/Tracy120/git.git
 - [deleted]         v1.0

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git tag

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$ git tag | xargs git tag -d

pc@DESKTOP-OTTEP0S MINGW64 ~/Documents/Advanced/merge-conflict-demo (main)
$
```
