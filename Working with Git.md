# Local Git STates
1. Working Directory ↓ 
2. Staging area ↓
3. Repository (.git folder) ↓
4. Remote Repository

##

# Git Commands

## To start a new project folder in github
```
$ git init demo 
```

"demo" will create "demo" folder with the initilized git repository in the current directory

## To add files to the git track
```
$ git status
$ git add .
$ git commit -m "Git Course"
```

## To delete a repository in Git, in the working directory
```
$ rm -rf .git
```

## To show the list of commits:
```
$ git log
commit a219a73f7c896d983182db3cc24f3722e634189c (HEAD -> master)
Author: Jacqueline Escalante <jacesca@gmail.com>
Date:   Tue Aug 30 14:23:04 2022 -0600

    Adding initial files to Git Course
```

This is like to have git history
```
$ git log --oneline --graph --decorate --all
* 6ea6aed (HEAD -> master) Second update in Git Course
* a219a73 Adding initial files to Git Course
```

or
```
$ git show
commit a219a73f7c896d983182db3cc24f3722e634189c (HEAD -> master)
Author: Jacqueline Escalante <jacesca@gmail.com>
Date:   Tue Aug 30 14:23:04 2022 -0600

    Adding initial files to Git Course

diff --git a/Installing Git.txt b/Installing Git.txt
new file mode 100644
index 0000000..4f5ad88
--- /dev/null
+++ b/Installing Git.txt
@@ -0,0 +1,81 @@
+Installing GIT
+*****
+***** Git for windows
+*****
+(1) https://git-scm.com/
+Download the last version
+
+(2) In git bash:
+>> git config --global user.name "Jacqueline Escalante"
+>> git config --global user.email "jacesca@gmail.com"
+
+*****
+***** Notepad ++
+*****
+(3) https://notepad-plus-plus.org/
+
+(4) Append it to the System's Path Variable
+In the explorer, look for "This PC"
+Click right and select Properties
+Select System on the left menu
+Select Advanced System Settings option (as tab) in the right side of the window
+Choose Advanced Tab
+Click on Environment Variables button
+Go to System Variables
+Look for Path
:
```
You can exit with "q"

## To see which files git is tracking
```
$ git ls-files
```

## Express Commit
To add modified files that are being tracked (Not works with untracked files) to the Git staging area
```
$ git commit -a
$ git commit -am "Example Update"
```

## To reset staging files
```
$ git reset HEAD README.md
Unstaged changes after reset:
M       README.md

$ git reset README.md
Unstaged changes after reset:
M       README.md
```

Note: a head is a ref that points to the tip (latest commit) of a branch


## To revert changes to last good commit executed
```
$ git checkout -- README.md (Do not work locally)
$ git checkout HEAD -- README.md
```

## To get help: 
git help <command>
```
$ git help log
```

git <command> --help
```
$ git log --help
```

## To create a new command with "git alias"
```
$ git config --global alias.history "log --oneline --graph --decorate --all"
```

Now you can use the alias
```
$ git history
* 6ea6aed (HEAD -> master) Second update in Git Course
* a219a73 Adding initial files to Git Course
```

Alias does not prevent to pass more parameters 
```
$ git history -- README.md
* 6ea6aed (HEAD -> master) Second update in Git Course
* a219a73 Adding initial files to Git Course
```
The additional parameters is just to return the commits where the "README.md" file is present.


## To review the global configuration
```
$ git config --global --list
user.name=Jacqueline Escalante
user.email=jacesca@gmail.com
core.editor=notepad++ -multiInst -nosession
diff.tool=p4merge
difftool.p4merge.path=c:/Program Files/Perforce/p4merge.exe
difftool.prompt=false
merge.tool=p4merge
mergetool.p4merge.path=c:/Program Files/Perforce/p4merge.exe
mergetool.prompt=false
alias.history=log --oneline --graph --decorate --all
```

Next command is to open the file where this global configuration is saved
```
$ git config --global -e
```

## To rename a file 

### To rename a file | Using Git
```
$ ls
README.md   example.txt

$ git mv example.txt demo.txt

$ ls
README.md   demo.txt

$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    example.txt -> demo.txt

$ git commit -m "Renaming files in Git Course"
[master 8e03dfb] Renaming files in Git Course
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename example.txt => demo.txt (100%)

```

### To rename a file | Outside Git
```
$ touch myfile.txt

$ ls
README.md   myfile.txt

$ git add myfile.txt
$ git commit -m "The myfile.txt was added to Git Course"

$ mv myfile.txt myfile.log

$ ls -l
total 229
-rw-r--r-- 1 jacesca 197121     78 Aug 30 15:01  README.md
-rw-r--r-- 1 jacesca 197121      0 Aug 30 17:32  myfile.log

$ git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    myfile.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        myfile.log

no changes added to commit (use "git add" and/or "git commit -a")

$ git status

$ git add -u #Only for updates
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    myfile.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        myfile.log
		
$ git add -A
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    myfile.txt -> myfile.log
		
$ git commit -m "Renaming myfile in Git Course"
[master 7abddd5] Renaming myfile in Git Course
 2 files changed, 83 insertions(+)
 rename myfile.txt => myfile.log (100%)

```

## To remove a file 

### To remove a file | Using Git
```
$ ls
README.md   demo.txt

$ git rm demo.txt
rm 'demo.txt'

$ ls
README.md

$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    demo.txt

$ git commit -m "Deleting demo file in Git Course"
[master d737204] Deleting demo file in Git Course
 1 file changed, 1 deletion(-)
 delete mode 100644 demo.txt
```

### To remove a file | Ouside Git
```
$ ls -l
total 229
-rw-r--r-- 1 jacesca 197121     78 Aug 30 15:01  README.md
-rw-r--r-- 1 jacesca 197121      0 Aug 30 17:32  myfile.log

$ rm myfile.log

$ ls -l
total 229
-rw-r--r-- 1 jacesca 197121     78 Aug 30 15:01  README.md

$ git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    myfile.log
no changes added to commit (use "git add" and/or "git commit -a")

$ git add -u
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    myfile.log
$ git commit -m "Removing myfile from Git course"
```

## To exclude files
```
$ ls -l
total 230
-rw-r--r-- 1 jacesca 197121     78 Aug 30 15:01  README.md
-rw-r--r-- 1 jacesca 197121     81 Aug 30 17:58  app.log

$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        app.log
nothing added to commit but untracked files present (use "git add" to track)

$ npp .gitignore

$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore

nothing added to commit but untracked files present (use "git add" to track)

$ git add .gitignore
$ git commit -m "Adding .gitignore to Git Course"
$ git status
On branch master
nothing to commit, working tree clean

$ ls -al
total 239
drwxr-xr-x 1 jacesca 197121      0 Aug 30 18:01  ./
drwxr-xr-x 1 jacesca 197121      0 Aug 30 10:43  ../
drwxr-xr-x 1 jacesca 197121      0 Aug 30 18:05  .git/
-rw-r--r-- 1 jacesca 197121      5 Aug 30 18:02  .gitignore
-rw-r--r-- 1 jacesca 197121     78 Aug 30 15:01  README.md
-rw-r--r-- 1 jacesca 197121     81 Aug 30 17:58  app.log
```
We add: "*.log" to the ".gitignore" file

## To see the differences between two commit points
```
$ git history
* d845615 (HEAD -> master) Update No.12 in Git Course
* 489a920 Adding .gitignore to Git Course
* 87e3ed0 Another update to documentation in Git Course
* 04ce9bb Removing myfile from Git course
* 7abddd5 Renaming myfile in Git Course
* 4f41760 The myfile.txt was added to Git Course
* d737204 Deleting demo file in Git Course
* 8e03dfb Renaming files in Git Course
* e8b4ab8 Adding example file to Git Course
* b736503 Adding md files to Git Course
* 2898aac Third commit in Git Course
* 6ea6aed Second update in Git Course
* a219a73 Adding initial files to Git Course

$ git diff 6ea6aed HEAD
diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000..bf0824e
--- /dev/null
+++ b/.gitignore
@@ -0,0 +1 @@
+*.log
\ No newline at end of file
diff --git a/Installing Git.md b/Installing Git.md
new file mode 100644
index 0000000..44d3fd8
--- /dev/null
+++ b/Installing Git.md
@@ -0,0 +1,71 @@
+# Installing GIT (Windows)
+
+## Git
+1. Go to https://git-scm.com/ and download the last Git version
+>- In the custom configuration, add the git icon to the desktop, allow use git from the window command prompt abd checkout as-is (unix style).
+
+2. In git bash:
+$ git config --global user.name "Jacqueline Escalante"
+$ git config --global user.email "jacesca@gmail.com"
+
+## Notepad++
+3. Install Notepad++ from https://notepad-plus-plus.org/
+
+4. Append it to the System's Path Variable
+>- In the explorer, look for "This PC"
+>- Click right and select Properties
+>- Select System on the left menu
+>- Select Advanced System Settings option (as tab) in the right side of the window
+>- Choose Advanced Tab
+>- Click on Environment Variables button
+>- Go to System Variables
:
```

## To see what is recently changed
```
$ npp README.md

$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
no changes added to commit (use "git add" and/or "git commit -a")

$ git diff
diff --git a/README.md b/README.md
index b0cf6d8..1c53031 100644
--- a/README.md
+++ b/README.md
@@ -3,4 +3,5 @@
 This is the readme file.

 # Update
-(Second version)
\ No newline at end of file
+(Second version)
+Adding some updates
\ No newline at end of file


$ git difftool
```

##

# Working with Branch

## To visualize the branches
```
$ git branch
* master
```
## To update changes on a different branch
```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
no changes added to commit (use "git add" and/or "git commit -a")

$ git checkout -b updates
Switched to a new branch 'updates'

$ git branch
  master
* updates

$ git status
On branch updates
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
no changes added to commit (use "git add" and/or "git commit -a")

$ git add .
$ git commit -m "Adding some updates on a branch for the Git course"
$ git status
On branch updates
nothing to commit, working tree clean

$ git history
* 4c641bb (HEAD -> updates) Adding some updates on a branch for the Git course
* d845615 (master) Update No.12 in Git Course
* 489a920 Adding .gitignore to Git Course
* 87e3ed0 Another update to documentation in Git Course
* 04ce9bb Removing myfile from Git course
* 7abddd5 Renaming myfile in Git Course
* 4f41760 The myfile.txt was added to Git Course
* d737204 Deleting demo file in Git Course
* 8e03dfb Renaming files in Git Course
* e8b4ab8 Adding example file to Git Course
* b736503 Adding md files to Git Course
* 2898aac Third commit in Git Course
* 6ea6aed Second update in Git Course
* a219a73 Adding initial files to Git Course
```

## To see differences between branches
```
$ git diff updates master
diff --git a/README.md b/README.md
index d243b5e..b0cf6d8 100644
--- a/README.md
+++ b/README.md
@@ -3,5 +3,4 @@
 This is the readme file.

 # Update
-(Second version)
-Adding some updates on a branch
\ No newline at end of file
+(Second version)
\ No newline at end of file
```

## To integrate changes in the master branch
```
$ git branch
  master
* updates

$ git checkout master
Switched to branch 'master'

$ git branch
* master
  updates

$ git history
* 4c641bb (updates) Adding some updates on a branch for the Git course
* d845615 (HEAD -> master) Update No.12 in Git Course
* 489a920 Adding .gitignore to Git Course
* 87e3ed0 Another update to documentation in Git Course
* 04ce9bb Removing myfile from Git course
* 7abddd5 Renaming myfile in Git Course
* 4f41760 The myfile.txt was added to Git Course
* d737204 Deleting demo file in Git Course
* 8e03dfb Renaming files in Git Course
* e8b4ab8 Adding example file to Git Course
* b736503 Adding md files to Git Course
* 2898aac Third commit in Git Course
* 6ea6aed Second update in Git Course
* a219a73 Adding initial files to Git Course
```

### Fast Forward
Make merge from a branch in the current branch
> p.e. master is the current branch, and updates will be the branch, as parameter, that we need to merge in the current brach
```
$ git merge updates
Updating d845615..4c641bb
Fast-forward
 README.md | 3 ++-
 1 file changed, 2 insertions(+), 1 deletion(-)
 
$ git history
* 4c641bb (HEAD -> master, updates) Adding some updates on a branch for the Git course
* d845615 Update No.12 in Git Course
* 489a920 Adding .gitignore to Git Course
* 87e3ed0 Another update to documentation in Git Course
* 04ce9bb Removing myfile from Git course
* 7abddd5 Renaming myfile in Git Course
* 4f41760 The myfile.txt was added to Git Course
* d737204 Deleting demo file in Git Course
* 8e03dfb Renaming files in Git Course
* e8b4ab8 Adding example file to Git Course
* b736503 Adding md files to Git Course
* 2898aac Third commit in Git Course
* 6ea6aed Second update in Git Course
* a219a73 Adding initial files to Git Course
```

We can delete the updates branch because that will not be needed anymore
```
$ git branch -d updates
Deleted branch updates (was 4c641bb).

$ git history
* 4c641bb (HEAD -> master) Adding some updates on a branch for the Git course
* d845615 Update No.12 in Git Course
* 489a920 Adding .gitignore to Git Course
* 87e3ed0 Another update to documentation in Git Course
* 04ce9bb Removing myfile from Git course
* 7abddd5 Renaming myfile in Git Course
* 4f41760 The myfile.txt was added to Git Course
* d737204 Deleting demo file in Git Course
* 8e03dfb Renaming files in Git Course
* e8b4ab8 Adding example file to Git Course
* b736503 Adding md files to Git Course
* 2898aac Third commit in Git Course
* 6ea6aed Second update in Git Course
* a219a73 Adding initial files to Git Course
```

## Dealing with conflicts
```
$ git status
On branch master
nothing to commit, working tree clean

$ git branch
* master

$ git checkout -b 'very-bad'
Switched to a new branch 'very-bad'

$ git branch -a
  master
* very-bad
```

Now we are going to update readme.md file in very-bad branch
```
$ npp README.md

$ git commit -am "Very-bad updates in Git course"
[very-bad 24fd142] Very-bad updates in Git course
 1 file changed, 1 insertion(+), 1 deletion(-)
 
$ git history
* 24fd142 (HEAD -> very-bad) Very-bad updates in Git course
* 4c641bb (master) Adding some updates on a branch for the Git course
* d845615 Update No.12 in Git Course
* 489a920 Adding .gitignore to Git Course
* 87e3ed0 Another update to documentation in Git Course
* 04ce9bb Removing myfile from Git course
* 7abddd5 Renaming myfile in Git Course
* 4f41760 The myfile.txt was added to Git Course
* d737204 Deleting demo file in Git Course
* 8e03dfb Renaming files in Git Course
* e8b4ab8 Adding example file to Git Course
* b736503 Adding md files to Git Course
* 2898aac Third commit in Git Course
* 6ea6aed Second update in Git Course
* a219a73 Adding initial files to Git Course
```

And then, we move again to Master branch and update readme.md file
```
$ git checkout master
Switched to branch 'master'

$ git branch -a
* master
  very-bad

$ npp README.md

$ git commit -am "Causing issues again in Git course"
[master 2a5d893] Causing issues again in Git course
 1 file changed, 1 insertion(+), 1 deletion(-)

$ git history
* 2a5d893 (HEAD -> master) Causing issues again in Git course
| * 24fd142 (very-bad) Very-bad updates in Git course
|/
* 4c641bb Adding some updates on a branch for the Git course
* d845615 Update No.12 in Git Course
* 489a920 Adding .gitignore to Git Course
* 87e3ed0 Another update to documentation in Git Course
* 04ce9bb Removing myfile from Git course
* 7abddd5 Renaming myfile in Git Course
* 4f41760 The myfile.txt was added to Git Course
* d737204 Deleting demo file in Git Course
* 8e03dfb Renaming files in Git Course
* e8b4ab8 Adding example file to Git Course
* b736503 Adding md files to Git Course
* 2898aac Third commit in Git Course
* 6ea6aed Second update in Git Course
* a219a73 Adding initial files to Git Course

$ git history
* 2a5d893 (HEAD -> master) Causing issues again in Git course
| * 24fd142 (very-bad) Very-bad updates in Git course
|/
* 4c641bb Adding some updates on a branch for the Git course
* d845615 Update No.12 in Git Course
* 489a920 Adding .gitignore to Git Course
* 87e3ed0 Another update to documentation in Git Course
* 04ce9bb Removing myfile from Git course
* 7abddd5 Renaming myfile in Git Course
* 4f41760 The myfile.txt was added to Git Course
* d737204 Deleting demo file in Git Course
* 8e03dfb Renaming files in Git Course
* e8b4ab8 Adding example file to Git Course
* b736503 Adding md files to Git Course
* 2898aac Third commit in Git Course
* 6ea6aed Second update in Git Course
* a219a73 Adding initial files to Git Course

$ git merge very-bad
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

Finally, let's go to merge now
```
$ git mergetool
Merging:
README.md

Normal merge conflict for 'README.md':
  {local}: modified file
  {remote}: modified file

$ git status
On branch master
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)
Changes to be committed:
        modified:   README.md


$ git commit -m "Resolving conflicts in Git course"
[master 848632c] Resolving conflicts in Git course

$ git status
On branch master
nothing to commit, working tree clean

$ git history
*   848632c (HEAD -> master) Resolving conflicts in Git course
|\
| * 4a2547c (very-bad) Updates in very-bad branch for Git course III
* | a749b44 Updates in master branch for Git course III
* | ff4dd3d Causing issues again in Git course III
* | 583c22d Causing issues again in Git course II
|\|
| * 24fd142 Very-bad updates in Git course
* | 2a5d893 Causing issues again in Git course
|/
* 4c641bb Adding some updates on a branch for the Git course
* d845615 Update No.12 in Git Course
* 489a920 Adding .gitignore to Git Course
* 87e3ed0 Another update to documentation in Git Course
* 04ce9bb Removing myfile from Git course
* 7abddd5 Renaming myfile in Git Course
* 4f41760 The myfile.txt was added to Git Course
* d737204 Deleting demo file in Git Course
* 8e03dfb Renaming files in Git Course
* e8b4ab8 Adding example file to Git Course
* b736503 Adding md files to Git Course
* 2898aac Third commit in Git Course
* 6ea6aed Second update in Git Course
* a219a73 Adding initial files to Git Course

```

## Setting milestones with tag

### Lightweight tags
There's no associated information with it
```
$ git tag --list

$ git tag mytag

$ git tag --list
mytag

$ git history
* 65b2496 (HEAD -> master, tag: mytag) Update on merge commands for Git Course
  ...
* 6ea6aed Second update in Git Course
* a219a73 Adding initial files to Git Course

```

To delete the tag
```
$ git tag -d mytag
Deleted tag 'mytag' (was 65b2496)

$ git history
* 65b2496 (HEAD -> master) Update on merge commands for Git Course
  ...
* 6ea6aed Second update in Git Course
* a219a73 Adding initial files to Git Course
```

### Annotated tags
These tags have extra information associated with them.
```
$ git tag -a v1.0 -m "Release 1.0"

$ git tag --list
v1.0

$ git history
* 65b2496 (HEAD -> master, tag: v1.0) Update on merge commands for Git Course
  ...
* 6ea6aed Second update in Git Course
* a219a73 Adding initial files to Git Course

$ git show v1.0
tag v1.0
Tagger: Jacqueline Escalante <jacesca@gmail.com>
Date:   Wed Aug 31 08:15:31 2022 -0600

Release 1.0

commit 65b249625d864db2d0b5892f3175e04a4f4a219a (HEAD -> master, tag: v1.0)
Author: Jacqueline Escalante <jacesca@gmail.com>
Date:   Tue Aug 30 23:54:07 2022 -0600

    Update on merge commands for Git Course

diff --git a/.gitignore b/.gitignore
  ...
:
```

# Stashing (WIP: Working in Progress)
```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
no changes added to commit (use "git add" and/or "git commit -a")

$ git stash
Saved working directory and index state WIP on master: f4d3c33 Updating the documentation in Git course

$ git stash list
stash@{0}: WIP on master: f4d3c33 Updating the documentation in Git course

$ git status
On branch master
nothing to commit, working tree clean

$ npp LICENSE.txt
$ git add .
$ git commit -m "Adding LICENSE file to Git Course"
$ git status
On branch master
nothing to commit, working tree clean

$ git stash pop
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (75ca6d68bbc4a87c218a99991841d59865ef14fb)

$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
no changes added to commit (use "git add" and/or "git commit -a")

$ git stash list
<--  Nothing to show, empty

$ git commit -am "Updating README file again in Git Course"
$ git status
On branch master
nothing to commit, working tree clean
```

# Reset and Reflog

## Reset
1. Soft reset :arrow_right: which is the least destructive of them all; basically, all it does is change where HEAD is pointing, preservint the Git staging area and our working directory. Effectively, we can back out our changes, make minor modifications to them, and then commit where head is currently pointing.
2. Mixed reset :arrow_right: which is the default value. This reset will unstage the number of changes.
3. Hard reset :arrow_right: which is the most destructive. It simply tells us that our HEAD is now at a new location,

### Soft Reset
```
$ git status
On branch master
nothing to commit, working tree clean

$ npp README.md <-- First Change
$ git add .

$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md


$ npp README.md <-- Second Change
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

$ git history
* f8c8a78 (HEAD -> master) Updating README file again in Git Course
* d0eb781 Adding LICENSE file to Git Course
* f4d3c33 Updating the documentation in Git course
* 65b2496 (tag: v1.0) Update on merge commands for Git Course

$ git reset f4d3c33 --soft
$ git history
* f4d3c33 (HEAD -> master) Updating the documentation in Git course
* 65b2496 (tag: v1.0) Update on merge commands for Git Course

$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   LICENSE.txt
        modified:   README.md
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
```

### Mixed reset
```
$ git history
* f4d3c33 (HEAD -> master) Updating the documentation in Git course
* 65b2496 (tag: v1.0) Update on merge commands for Git Course
*   848632c Resolving conflicts in Git course
|\
| * 4a2547c (very-bad) Updates in very-bad branch for Git course III
* | a749b44 Updates in master branch for Git course III
* | ff4dd3d Causing issues again in Git course III
* | 583c22d Causing issues again in Git course II
|\|
| * 24fd142 Very-bad updates in Git course
* | 2a5d893 Causing issues again in Git course
|/
* 4c641bb Adding some updates on a branch for the Git course
* d845615 Update No.12 in Git Course
* 489a920 Adding .gitignore to Git Course
* 87e3ed0 Another update to documentation in Git Course
* 04ce9bb Removing myfile from Git course
* 7abddd5 Renaming myfile in Git Course
* 4f41760 The myfile.txt was added to Git Course
* d737204 Deleting demo file in Git Course
* 8e03dfb Renaming files in Git Course
* e8b4ab8 Adding example file to Git Course
* b736503 Adding md files to Git Course
* 2898aac Third commit in Git Course
* 6ea6aed Second update in Git Course
* a219a73 Adding initial files to Git Course

$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   LICENSE.txt
        modified:   README.md
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

$ git reset 489a920 --mixed
Unstaged changes after reset:
M       .gitignore
M       Installing Git.md
M       README.md
M       Working with Git.md

$ git history
* 65b2496 (tag: v1.0) Update on merge commands for Git Course
*   848632c Resolving conflicts in Git course
|\
| * 4a2547c (very-bad) Updates in very-bad branch for Git course III
* | a749b44 Updates in master branch for Git course III
* | ff4dd3d Causing issues again in Git course III
* | 583c22d Causing issues again in Git course II
|\|
| * 24fd142 Very-bad updates in Git course
* | 2a5d893 Causing issues again in Git course
|/
* 4c641bb Adding some updates on a branch for the Git course
* d845615 Update No.12 in Git Course
* 489a920 (HEAD -> master) Adding .gitignore to Git Course
* 87e3ed0 Another update to documentation in Git Course
* 04ce9bb Removing myfile from Git course
* 7abddd5 Renaming myfile in Git Course
* 4f41760 The myfile.txt was added to Git Course
* d737204 Deleting demo file in Git Course
* 8e03dfb Renaming files in Git Course
* e8b4ab8 Adding example file to Git Course
* b736503 Adding md files to Git Course
* 2898aac Third commit in Git Course
* 6ea6aed Second update in Git Course
* a219a73 Adding initial files to Git Course

$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   .gitignore
        modified:   Installing Git.md
        modified:   README.md
        modified:   Working with Git.md
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        LICENSE.txt
no changes added to commit (use "git add" and/or "git commit -a")
```

### Hard reset
```
$ git reset 6ea6aed --hard
HEAD is now at 6ea6aed Second update in Git Course

$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        LICENSE.txt
        app.log
nothing added to commit but untracked files present (use "git add" to track)

$ git history
* 65b2496 (tag: v1.0) Update on merge commands for Git Course
*   848632c Resolving conflicts in Git course
|\
| * 4a2547c (very-bad) Updates in very-bad branch for Git course III
* | a749b44 Updates in master branch for Git course III
* | ff4dd3d Causing issues again in Git course III
* | 583c22d Causing issues again in Git course II
|\|
| * 24fd142 Very-bad updates in Git course
* | 2a5d893 Causing issues again in Git course
|/
* 4c641bb Adding some updates on a branch for the Git course
* d845615 Update No.12 in Git Course
* 489a920 Adding .gitignore to Git Course
* 87e3ed0 Another update to documentation in Git Course
* 04ce9bb Removing myfile from Git course
* 7abddd5 Renaming myfile in Git Course
* 4f41760 The myfile.txt was added to Git Course
* d737204 Deleting demo file in Git Course
* 8e03dfb Renaming files in Git Course
* e8b4ab8 Adding example file to Git Course
* b736503 Adding md files to Git Course
* 2898aac Third commit in Git Course
* 6ea6aed (HEAD -> master) Second update in Git Course
* a219a73 Adding initial files to Git Course

$ git log --oneline
6ea6aed (HEAD -> master) Second update in Git Course
a219a73 Adding initial files to Git Course
```

## Reflog
- It is not simmilar to "git log". 
- "git log" shows us our commit ids.
- "git reflog" shows us all the different actions we have taken while in this repository. This allows us to get all the way back to a specific commit id if we need to.
```
$ git reflog
6ea6aed (HEAD -> master) HEAD@{0}: reset: moving to 6ea6aed
b736503 HEAD@{1}: reset: moving to b736503
489a920 HEAD@{2}: reset: moving to 489a920
f4d3c33 HEAD@{3}: reset: moving to f4d3c33
d0eb781 HEAD@{4}: reset: moving to d0eb781
f8c8a78 HEAD@{5}: commit: Updating README file again in Git Course
d0eb781 HEAD@{6}: commit: Adding LICENSE file to Git Course
f4d3c33 HEAD@{7}: reset: moving to HEAD
f4d3c33 HEAD@{8}: commit: Updating the documentation in Git course
65b2496 (tag: v1.0) HEAD@{9}: commit: Update on merge commands for Git Course
848632c HEAD@{10}: commit (merge): Resolving conflicts in Git course
a749b44 HEAD@{11}: commit: Updates in master branch for Git course III
ff4dd3d HEAD@{12}: checkout: moving from very-bad to master
4a2547c (very-bad) HEAD@{13}: commit: Updates in very-bad branch for Git course III
24fd142 HEAD@{14}: checkout: moving from master to very-bad
ff4dd3d HEAD@{15}: commit: Causing issues again in Git course III
583c22d HEAD@{16}: commit (merge): Causing issues again in Git course II
2a5d893 HEAD@{17}: commit: Causing issues again in Git course
4c641bb HEAD@{18}: checkout: moving from very-bad to master
24fd142 HEAD@{19}: commit: Very-bad updates in Git course
4c641bb HEAD@{20}: checkout: moving from master to very-bad
4c641bb HEAD@{21}: merge updates: Fast-forward
d845615 HEAD@{22}: checkout: moving from updates to master
4c641bb HEAD@{23}: commit: Adding some updates on a branch for the Git course
d845615 HEAD@{24}: checkout: moving from master to updates
d845615 HEAD@{25}: commit: Update No.12 in Git Course
489a920 HEAD@{26}: commit: Adding .gitignore to Git Course
87e3ed0 HEAD@{27}: commit: Another update to documentation in Git Course
04ce9bb HEAD@{28}: commit: Removing myfile from Git course
7abddd5 HEAD@{29}: commit: Renaming myfile in Git Course
4f41760 HEAD@{30}: commit: The myfile.txt was added to Git Course
d737204 HEAD@{31}: commit: Deleting demo file in Git Course
8e03dfb HEAD@{32}: commit: Renaming files in Git Course
e8b4ab8 HEAD@{33}: commit: Adding example file to Git Course
b736503 HEAD@{34}: commit: Adding md files to Git Course
2898aac HEAD@{35}: commit: Third commit in Git Course
6ea6aed (HEAD -> master) HEAD@{36}: reset: moving to HEAD
6ea6aed (HEAD -> master) HEAD@{37}: reset: moving to HEAD
: 

$ git reset --hard f8c8a78
HEAD is now at f8c8a78 Updating README file again in Git Course

$ git status
On branch master
nothing to commit, working tree clean

$ git log --oneline
f8c8a78 (HEAD -> master) Updating README file again in Git Course
d0eb781 Adding LICENSE file to Git Course
f4d3c33 Updating the documentation in Git course
65b2496 (tag: v1.0) Update on merge commands for Git Course
848632c Resolving conflicts in Git course
a749b44 Updates in master branch for Git course III
4a2547c (very-bad) Updates in very-bad branch for Git course III
ff4dd3d Causing issues again in Git course III
583c22d Causing issues again in Git course II
2a5d893 Causing issues again in Git course
24fd142 Very-bad updates in Git course
4c641bb Adding some updates on a branch for the Git course
d845615 Update No.12 in Git Course
489a920 Adding .gitignore to Git Course
87e3ed0 Another update to documentation in Git Course
04ce9bb Removing myfile from Git course
7abddd5 Renaming myfile in Git Course
4f41760 The myfile.txt was added to Git Course
d737204 Deleting demo file in Git Course
8e03dfb Renaming files in Git Course
e8b4ab8 Adding example file to Git Course
b736503 Adding md files to Git Course
2898aac Third commit in Git Course
6ea6aed Second update in Git Course
a219a73 Adding initial files to Git Course
```

##

# Other commands

## To see all the files and folders that are part of a repository
```
$ ls -al
```
If you only "use git commit", as we are already configured Notepad, an editor will be open to add the information we want to name this commit. Once we add the description we want (First line), we close the editor and return to the git bash.

## To clear the command window
```
$ clear
```

## To create a new file
```
$ touch new.file
```

## To delete a file
```
$ rm new.file
```

## To display the content of a file
```
$ cat Readme.md
## Example file
# Tracking
This is the readme file.

# Update
(Second version)
<<<<<<< HEAD
Hope this is not a problem.
=======
This is bound to cause troubles.
>>>>>>> very-bad
```

##

# Other

## To stop .bak file creation in notepad++
Open Notepad++ and go to Settings=>Preferences=>Backup than select “None” from Backup on save. 
