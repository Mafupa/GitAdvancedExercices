# Part 1: Refining Git History (10 Challenges)

## Missing File Fix
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git log
commit 95e3501966ed6062d79e7fe80cbd0fd2131bea57 (HEAD -> main)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:19 2025 +0200

    chore: Create third and fourth files

commit 7ce5af08e074c10881781958466d2ba5746340e2
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:18 2025 +0200

    chore: Create another file

commit 3acc09c9a2c60fd20912acc364b676296a16cb0e
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:18 2025 +0200

    chore: Create initial file

commit cafce56de22dcd8f056c1881a3689a6099d055c5 (origin/main, origin/HEAD)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Feb 25 12:07:25 2025 +0200

    Repo creation

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git add test4.md

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git commit --amend -m "Create third and fourth files but appropriate"
[main e17fd71] Create third and fourth files but appropriate
 Date: Tue Mar 4 10:41:19 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md
```
## Editing Commit History
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git rebase -i HEAD~2
Stopped at 7ce5af0...  chore: Create another file
You can amend the commit now, with

  git commit --amend

Once you are satisfied with your changes, run

  git rebase --continue

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git commit --amend -m "Create second file"
[detached HEAD 0a11a04] Create second file
 Date: Tue Mar 4 10:41:18 2025 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git rebase --continue
Successfully rebased and updated refs/heads/main.

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git log
commit d438df73036e53237da388342084457d2f324b29 (HEAD -> main)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:19 2025 +0200

    Create third and fourth files but appropriate

commit 0a11a04c3ba749188c37ad5b207936d4f785b4d9
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:18 2025 +0200

    Create second file

commit 3acc09c9a2c60fd20912acc364b676296a16cb0e
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:18 2025 +0200

    chore: Create initial file

commit cafce56de22dcd8f056c1881a3689a6099d055c5 (origin/main, origin/HEAD)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Feb 25 12:07:25 2025 +0200

    Repo creation
```
## Keeping History Tidy - Squashing Commits
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git rebase -i HEAD~3
[detached HEAD 6ca294a] chore: Create initial file
 Date: Tue Mar 4 10:41:18 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git log
commit 619e46a5c9a2f4080b01fd5e50b6ae2ec0952e04 (HEAD -> main)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:19 2025 +0200

    Create third and fourth files but appropriate

commit 6ca294ad5f0596f1390e50b994468f8c6c926ba2
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:18 2025 +0200

    chore: Create initial file

commit cafce56de22dcd8f056c1881a3689a6099d055c5 (origin/main, origin/HEAD)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Feb 25 12:07:25 2025 +0200

    Repo creation

```
## Splitting a Commit
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git reset HEAD~

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test3.md
        test4.md

nothing added to commit but untracked files present (use "git add" to track)

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git add test3.md

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git commit -m "Create third file"
[main 46cfd5e] Create third file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git add test4.md

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git commit -m "Create fourth file"
[main 2da9155] Create fourth file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git log
commit 2da91551c130cb826e2a3416b62bd46c5cbf2911 (HEAD -> main)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:47:37 2025 +0200

    Create fourth file

commit 46cfd5e3f9f9a63223f49f52ac266c3fac798824
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:47:23 2025 +0200

    Create third file

commit 6ca294ad5f0596f1390e50b994468f8c6c926ba2
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:18 2025 +0200

    chore: Create initial file

commit cafce56de22dcd8f056c1881a3689a6099d055c5 (origin/main, origin/HEAD)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Feb 25 12:07:25 2025 +0200

    Repo creation
```
## Advanced Squashing
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git rebase -i HEAD~2
[detached HEAD eb87511] Create third and fourth file
 Date: Tue Mar 4 10:47:23 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md
Successfully rebased and updated refs/heads/main.

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git log
commit eb87511176479dbdaa047f024ea906eebd55a07f (HEAD -> main)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:47:23 2025 +0200

    Create third and fourth file

commit 6ca294ad5f0596f1390e50b994468f8c6c926ba2
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:18 2025 +0200

    chore: Create initial file

commit cafce56de22dcd8f056c1881a3689a6099d055c5 (origin/main, origin/HEAD)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Feb 25 12:07:25 2025 +0200

    Repo creation

```
## Dropping a Commit
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>vim unwanted.txt

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git add unwanted.txt
warning: in the working copy of 'unwanted.txt', LF will be replaced by CRLF the next time Git touches it

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git commit -m "Unwanted commit"
[main 52e4bf1] Unwanted commit
 1 file changed, 1 insertion(+)
 create mode 100644 unwanted.txt

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git rebase -i
Successfully rebased and updated refs/heads/main.

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git log
commit eb87511176479dbdaa047f024ea906eebd55a07f (HEAD -> main)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:47:23 2025 +0200

    Create third and fourth file

commit 6ca294ad5f0596f1390e50b994468f8c6c926ba2
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:18 2025 +0200

    chore: Create initial file

commit cafce56de22dcd8f056c1881a3689a6099d055c5 (origin/main, origin/HEAD)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Feb 25 12:07:25 2025 +0200

    Repo creation

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git status
On branch main
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```
## Reordering Commits
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git rebase -i
Successfully rebased and updated refs/heads/main.

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git log
commit b4ac5ff02e2163f99d9b8a43c6a124a446cbb1e1 (HEAD -> main)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:18 2025 +0200

    chore: Create initial file

commit 8735b031621e5c484bd5723a0daafb9c31e38874
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:47:23 2025 +0200

    Create third and fourth file

commit cafce56de22dcd8f056c1881a3689a6099d055c5 (origin/main, origin/HEAD)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Feb 25 12:07:25 2025 +0200

    Repo creation

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git rebase -i
Successfully rebased and updated refs/heads/main.

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git log
commit 293704564f639cad4c776a61572fe97362afdcec (HEAD -> main)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:47:23 2025 +0200

    Create third and fourth file

commit d85c792d93b206bfd29d95d19da02ba905981a08
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:18 2025 +0200

    chore: Create initial file

commit cafce56de22dcd8f056c1881a3689a6099d055c5 (origin/main, origin/HEAD)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Feb 25 12:07:25 2025 +0200

    Repo creation
```
## Cherry-Picking Commits
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git checkout -b ft/branch
Switched to a new branch 'ft/branch'

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>vim test5.md

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git add test5.md
warning: in the working copy of 'test5.md', LF will be replaced by CRLF the next time Git touches it

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git commit -m "Implemented test 5"
[ft/branch ce960d3] Implemented test 5
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git branch
* ft/branch
  main

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git checkout -b main
fatal: a branch named 'main' already exists

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git checkout ft/branch
Switched to branch 'ft/branch'

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git log
commit ce960d31d0c0a8b41c1aaf60eb1cf043fce1c805 (HEAD -> ft/branch)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:57:24 2025 +0200

    Implemented test 5

commit 293704564f639cad4c776a61572fe97362afdcec (main)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:47:23 2025 +0200

    Create third and fourth file

commit d85c792d93b206bfd29d95d19da02ba905981a08
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 10:41:18 2025 +0200

    chore: Create initial file

commit cafce56de22dcd8f056c1881a3689a6099d055c5 (origin/main, origin/HEAD)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Feb 25 12:07:25 2025 +0200

    Repo creation

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git cherry-pick ce960d31d0c0a8b41c1aaf60eb1cf043fce1c805
[main 82d356b] Implemented test 5
 Date: Tue Mar 4 10:57:24 2025 +0200
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md

C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git log
commit 82d356b32242519c7a7a51271ff4bba42a126359 (HEAD -> main)
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

commit cafce56de22dcd8f056c1881a3689a6099d055c5 (origin/main, origin/HEAD)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Feb 25 12:07:25 2025 +0200

    Repo creation
```
## Visualizing Commit History
```cmd
C:\Users\ryank\Documents\Learn\THEGYM\GitAdvancedExercices>git log --graph
* commit 82d356b32242519c7a7a51271ff4bba42a126359 (HEAD -> main)
| Author: Mafupa <ryankarera@gmail.com>
| Date:   Tue Mar 4 10:57:24 2025 +0200
|
|     Implemented test 5
|
* commit 293704564f639cad4c776a61572fe97362afdcec
| Author: Mafupa <ryankarera@gmail.com>
| Date:   Tue Mar 4 10:47:23 2025 +0200
|
|     Create third and fourth file
|
* commit d85c792d93b206bfd29d95d19da02ba905981a08
| Author: Mafupa <ryankarera@gmail.com>
| Date:   Tue Mar 4 10:41:18 2025 +0200
|
|     chore: Create initial file
|
* commit cafce56de22dcd8f056c1881a3689a6099d055c5 (origin/main, origin/HEAD)
  Author: Mafupa <ryankarera@gmail.com>
  Date:   Tue Feb 25 12:07:25 2025 +0200

      Repo creation
```

