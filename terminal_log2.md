# Part 2: Branching Basics (10 Challenges)

## Feature Branch Creation
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git checkout -b ft/new-feature
Switched to a new branch 'ft/new-feature'
```
## Working on the Feature Branch
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>vim feature.txt

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git add feature.txt
warning: in the working copy of 'feature.txt', LF will be replaced by CRLF the next time Git touches it

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git commit -m "Implemented core functionality for new feature"
[ft/new-feature 19c1330] Implemented core functionality for new feature
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt
```
## Switching Back and Making More Changes
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>vim readme.txt

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git add readme.txt
warning: in the working copy of 'readme.txt', LF will be replaced by CRLF the next time Git touches it

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git commit -m "Updated project readme"
[main 6ab38f0] Updated project readme
 1 file changed, 1 insertion(+)
 create mode 100644 readme.txt
```
## Local vs. Remote Branches

## Branch Deletion
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git merge ft/new-feature
Merge made by the 'ort' strategy.
 feature.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git branch -d ft/new-feature
Deleted branch ft/new-feature (was 19c1330).
```
## Creating a Branch from a Commit
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git log
commit c457f0b0a59d2c14435a31aa33a8f14a186bea85 (HEAD -> main)
Merge: 6ab38f0 19c1330
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 11:17:48 2025 +0200

    Merge branch 'ft/new-feature'

commit 6ab38f000ceb92224ea1a218e9b966dea8f1c3b1
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 11:13:43 2025 +0200

    Updated project readme
commit c457f0b0a59d2c14435a31aa33a8f14a186bea85 (HEAD -> main)
Merge: 6ab38f0 19c1330
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 11:17:48 2025 +0200

    Merge branch 'ft/new-feature'

commit 6ab38f000ceb92224ea1a218e9b966dea8f1c3b1
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 11:13:43 2025 +0200

    Updated project readme

commit 19c133085cb8bf9cc55c8ca7924f36bc50639171
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 11:12:30 2025 +0200

    Implemented core functionality for new feature

commit 34ec9500718b780187052c0c65e5c0924d841990 (origin/main, origin/HEAD)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 11:05:43 2025 +0200

    terminal_log update

commit 82d356b32242519c7a7a51271ff4bba42a126359
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:57:24 2025 +0200

    Implemented test 5

commit 293704564f639cad4c776a61572fe97362afdcec
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:47:23 2025 +0200

    Create third and fourth file

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git checkout -b ft/new-branch-from-commit 19c133085cb8bf9cc55c8ca7924f36bc50639171
Switched to a new branch 'ft/new-branch-from-commit'

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git log
commit 19c133085cb8bf9cc55c8ca7924f36bc50639171 (HEAD -> ft/new-branch-from-commit)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 11:12:30 2025 +0200

    Implemented core functionality for new feature

commit 34ec9500718b780187052c0c65e5c0924d841990 (origin/main, origin/HEAD)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 11:05:43 2025 +0200

    terminal_log update

commit 82d356b32242519c7a7a51271ff4bba42a126359
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:57:24 2025 +0200

    Implemented test 5

commit 293704564f639cad4c776a61572fe97362afdcec
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:47:23 2025 +0200

    Create third and fourth file

commit d85c792d93b206bfd29d95d19da02ba905981a08
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:18 2025 +0200

    chore: Create initial file

commit cafce56de22dcd8f056c1881a3689a6099d055c5
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Feb 25 12:07:25 2025 +0200

    Repo creation
```
## Branch Merging
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git merge ft/new-branch-from-commit
Already up to date.

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git checkout ft/new-branch-from-commit
Switched to branch 'ft/new-branch-from-commit'
```
## Branch Rebasing
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git rebase -i main
Successfully rebased and updated refs/heads/ft/new-branch-from-commit.
```
## Renaming Branches
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git branch -m ft/new-branch-from-commit ft/improved-branch-name

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git branch
  ft/branch
  ft/improved-branch-name
* main

```
## Checking Out Detached HEAD
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git log
commit c457f0b0a59d2c14435a31aa33a8f14a186bea85 (HEAD -> main, ft/improved-branch-name)
Merge: 6ab38f0 19c1330
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 11:17:48 2025 +0200

    Merge branch 'ft/new-feature'

commit 6ab38f000ceb92224ea1a218e9b966dea8f1c3b1
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 11:13:43 2025 +0200

    Updated project readme

commit 19c133085cb8bf9cc55c8ca7924f36bc50639171
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 11:12:30 2025 +0200

    Implemented core functionality for new feature

commit 34ec9500718b780187052c0c65e5c0924d841990 (origin/main, origin/HEAD)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 11:05:43 2025 +0200

    terminal_log update

commit 82d356b32242519c7a7a51271ff4bba42a126359
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:57:24 2025 +0200

    Implemented test 5

commit 293704564f639cad4c776a61572fe97362afdcec
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:47:23 2025 +0200

    Create third and fourth file

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git checkout 19c133085cb8bf9cc55c8ca7924f36bc50639171
Note: switching to '19c133085cb8bf9cc55c8ca7924f36bc50639171'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 19c1330 Implemented core functionality for new feature

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git status
HEAD detached at 19c1330
nothing to commit, working tree clean

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>ls
README.md  feature.txt  terminal_log  test1.md  test2.md  test3.md  test4.md  test5.md

```
