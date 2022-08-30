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

##

# Other

## To stop .bak file creation in notepad++
Open Notepad++ and go to Settings=>Preferences=>Backup than select “None” from Backup on save. 
