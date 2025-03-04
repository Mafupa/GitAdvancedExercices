# Part 3: Advanced Workflows (10+ Challenges)

## Stashing Changes:
```cmd
gymamahoro@Amahoros-iMac GitAdvancedExercices % vim somechanges.txt 
gymamahoro@Amahoros-iMac GitAdvancedExercices % git add somechanges.txt 
gymamahoro@Amahoros-iMac GitAdvancedExercices % git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   somechanges.txt

gymamahoro@Amahoros-iMac GitAdvancedExercices % git stash
Saved working directory and index state WIP on main: 54b6a2d terminal_log2 update
gymamahoro@Amahoros-iMac GitAdvancedExercices % git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
gymamahoro@Amahoros-iMac GitAdvancedExercices %
```
## Retrieving Stashed Changes:
```cmd
gymamahoro@Amahoros-iMac GitAdvancedExercices % git stash pop
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   somechanges.txt

Dropped refs/stash@{0} (7b28159fcd3c9a33b38d109a6e8e2cefa5f4c034)
gymamahoro@Amahoros-iMac GitAdvancedExercices %
```
## Branch Merging Conflicts (Continued):
```cmd
gymamahoro@Amahoros-iMac GitAdvancedExercices % git add somechanges.txt 
gymamahoro@Amahoros-iMac GitAdvancedExercices % git checkout ft/new-feature
A	somechanges.txt
Switched to branch 'ft/new-feature'
gymamahoro@Amahoros-iMac GitAdvancedExercices % cat somechanges.txt 
somechanges on main
gymamahoro@Amahoros-iMac GitAdvancedExercices % vim somechanges.txt 
gymamahoro@Amahoros-iMac GitAdvancedExercices % git add somechanges.txt 
gymamahoro@Amahoros-iMac GitAdvancedExercices % git commit -m "some changes on new feature"
[ft/new-feature 0e0b5ed] some changes on new feature
 1 file changed, 1 insertion(+)
 create mode 100644 somechanges.txt
gymamahoro@Amahoros-iMac GitAdvancedExercices % cat somechanges.txt 
somechanges on new feature
gymamahoro@Amahoros-iMac GitAdvancedExercices % git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
gymamahoro@Amahoros-iMac GitAdvancedExercices % ls        
README.md	readme.txt	terminal_log2	test2.md	test4.md
feature.txt	terminal_log	test1.md	test3.md	test5.md
gymamahoro@Amahoros-iMac GitAdvancedExercices % vim somechanges.txt
gymamahoro@Amahoros-iMac GitAdvancedExercices % cat somechanges.txt 
some changes on main
gymamahoro@Amahoros-iMac GitAdvancedExercices % git add somechanges.txt 
gymamahoro@Amahoros-iMac GitAdvancedExercices % git commit -m "some changes on main"
[main dbc5142] some changes on main
 1 file changed, 1 insertion(+)
 create mode 100644 somechanges.txt
gymamahoro@Amahoros-iMac GitAdvancedExercices % git merge ft/new-feature
Auto-merging somechanges.txt
CONFLICT (add/add): Merge conflict in somechanges.txt
Automatic merge failed; fix conflicts and then commit the result.
gymamahoro@Amahoros-iMac GitAdvancedExercices % vim somechanges.txt 
gymamahoro@Amahoros-iMac GitAdvancedExercices % git add somechanges.txt 
gymamahoro@Amahoros-iMac GitAdvancedExercices % git commit
[main ecda071] Merge branch 'ft/new-feature'
gymamahoro@Amahoros-iMac GitAdvancedExercices %
```
## Resolving Merge Conflicts with a Merge Tool:
```cmd
gymamahoro@Amahoros-iMac GitAdvancedExercices % git mergetool
No files need merging
gymamahoro@Amahoros-iMac GitAdvancedExercices % git checkout ft/new-feature
Switched to branch 'ft/new-feature'
gymamahoro@Amahoros-iMac GitAdvancedExercices % vim somechanges.txt 
gymamahoro@Amahoros-iMac GitAdvancedExercices % cat somechanges.txt 
somechanges on new feature again
gymamahoro@Amahoros-iMac GitAdvancedExercices % git add somechanges.txt 
gymamahoro@Amahoros-iMac GitAdvancedExercices % git commit -m "somechanges on new feature again"
[ft/new-feature ddc2c94] somechanges on new feature again
 1 file changed, 1 insertion(+), 1 deletion(-)
gymamahoro@Amahoros-iMac GitAdvancedExercices % git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)
gymamahoro@Amahoros-iMac GitAdvancedExercices % cat somechanges.txt 
somechanges on new feature
gymamahoro@Amahoros-iMac GitAdvancedExercices % vim somechanges.txt 
gymamahoro@Amahoros-iMac GitAdvancedExercices % cat somechanges.txt 
somechanges on main again
gymamahoro@Amahoros-iMac GitAdvancedExercices % git add somechanges.txt 
gymamahoro@Amahoros-iMac GitAdvancedExercices % git commit -m "some changes on main again"
[main 86d4137] some changes on main again
 1 file changed, 1 insertion(+), 1 deletion(-)
gymamahoro@Amahoros-iMac GitAdvancedExercices % git merge ft/new-feature
Auto-merging somechanges.txt
CONFLICT (content): Merge conflict in somechanges.txt
Automatic merge failed; fix conflicts and then commit the result.
gymamahoro@Amahoros-iMac GitAdvancedExercices % git mergetool
Merging:
somechanges.txt

Normal merge conflict for 'somechanges.txt':
  {local}: modified file
  {remote}: modified file
4 files to edit
gymamahoro@Amahoros-iMac GitAdvancedExercices % git commit
[main c2d69ce] Merge branch 'ft/new-feature'
```
## Understanding Detached HEAD State:
```cmd
gymamahoro@Amahoros-iMac GitAdvancedExercices % git log -n 3
commit c2d69ce49d8b8ddcf2ee66fa260c66732e3b09a1 (HEAD -> main)
Merge: 86d4137 ddc2c94
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 13:16:24 2025 +0200

    Merge branch 'ft/new-feature'

commit 86d4137f8237da2b4b6caf5ede8b34a17eafff2b
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 13:15:06 2025 +0200

    some changes on main again

commit ddc2c944a220b810545accf41151c190557c6a27 (ft/new-feature)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 13:14:04 2025 +0200

    somechanges on new feature again
gymamahoro@Amahoros-iMac GitAdvancedExercices % git checkout c2d69ce49d8b8ddcf2ee66fa260c66732e3b09a1
Note: switching to 'c2d69ce49d8b8ddcf2ee66fa260c66732e3b09a1'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at c2d69ce Merge branch 'ft/new-feature'
gymamahoro@Amahoros-iMac GitAdvancedExercices % git branch
* (HEAD detached at c2d69ce)
  ft/new-feature
  main
gymamahoro@Amahoros-iMac GitAdvancedExercices % git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 6 commits.
  (use "git push" to publish your local commits)
gymamahoro@Amahoros-iMac GitAdvancedExercices % git branch
  ft/new-feature
* main
gymamahoro@Amahoros-iMac GitAdvancedExercices %
```
## Ignoring Files/Directories:
```cmd
gymamahoro@Amahoros-iMac GitAdvancedExercices % vim .gitignore
gymamahoro@Amahoros-iMac GitAdvancedExercices % cat .gitignore 
/tmp
gymamahoro@Amahoros-iMac GitAdvancedExercices % mkdir tmp
gymamahoro@Amahoros-iMac GitAdvancedExercices % git add .
gymamahoro@Amahoros-iMac GitAdvancedExercices % git status
On branch main
Your branch is ahead of 'origin/main' by 6 commits.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   .gitignore

gymamahoro@Amahoros-iMac GitAdvancedExercices %
```
## Working with Tags:
```cmd
gymamahoro@Amahoros-iMac GitAdvancedExercices % git tag v1.0

```
## Listing and Deleting Tags:
```cmd
gymamahoro@Amahoros-iMac GitAdvancedExercices % git tag
v1.0
gymamahoro@Amahoros-iMac GitAdvancedExercices % git show
commit dce4a8754298eec45252be971f465dcf0da7a820 (HEAD -> main, tag: v1.0)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 13:26:56 2025 +0200

    Added gitignore

diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000..ceeb05b
--- /dev/null
+++ b/.gitignore
@@ -0,0 +1 @@
+/tmp
gymamahoro@Amahoros-iMac GitAdvancedExercices %   
gymamahoro@Amahoros-iMac GitAdvancedExercices % git log
commit dce4a8754298eec45252be971f465dcf0da7a820 (HEAD -> main, tag: v1.0)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 13:26:56 2025 +0200

    Added gitignore
...
gymamahoro@Amahoros-iMac GitAdvancedExercices % git tag --d v1.0
Deleted tag 'v1.0' (was dce4a87)
gymamahoro@Amahoros-iMac GitAdvancedExercices % git log -n 1
commit dce4a8754298eec45252be971f465dcf0da7a820 (HEAD -> main)
Author: Mafupa <ryankarera@gmail.com>
Date:   Tue Mar 4 13:26:56 2025 +0200

    Added gitignore
gymamahoro@Amahoros-iMac GitAdvancedExercices %
```
## Pushing Local Work to Remote Repositories:
```cmd
gymamahoro@Amahoros-iMac GitAdvancedExercices % git push
Enumerating objects: 18, done.
Counting objects: 100% (18/18), done.
Delta compression using up to 8 threads
Compressing objects: 100% (12/12), done.
Writing objects: 100% (17/17), 1.56 KiB | 1.56 MiB/s, done.
Total 17 (delta 6), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (6/6), completed with 1 local object.
To https://github.com/Mafupa/GitAdvancedExercices.git
   54b6a2d..dce4a87  main -> main
gymamahoro@Amahoros-iMac GitAdvancedExercices %
```
## Pulling Changes from Remote Repositories:


