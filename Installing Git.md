# Installing GIT (Windows)

## Git
1. Go to https://git-scm.com/ and download the last Git version
>- In the custom configuration, add the git icon to the desktop, allow use git from the window command prompt abd checkout as-is (unix style).

2. In git bash:
```
$ git config --global user.name "Jacqueline Escalante"
$ git config --global user.email "jacesca@gmail.com"
```

## Notepad++
3. Install Notepad++ from https://notepad-plus-plus.org/

4. Append it to the System's Path Variable
>- In the explorer, look for "This PC"
>- Click right and select Properties
>- Select System on the left menu
>- Select Advanced System Settings option (as tab) in the right side of the window
>- Choose Advanced Tab
>- Click on Environment Variables button
>- Go to System Variables
>- Look for Path
>- Click on Edit Button
>- Add "C:\Program Files\Notepad++"
>- Click on OK (thrice)

5. Restart GitBash
6. Create/Update ~/.bash_profile
```
$ notepad++ ~/.bash_profile
```

On the file add the following line
```
alias npp='notepad++ -multiInst -nosession'
```

Then you can use "npp" instead of notepad++
Older version use .bashrc instead of .bash_profile

7. Make notepad++ the default editor
```
$ git config --global core.editor "notepad++ -multiInst -nosession"
```

You can review the globla configuration with the following command:
```
$ git config --global -e
```

## P4Merge
A visual compare and merge tool

8. Go to https://www.perforce.com/
>- Click on Downloads
>- Look for Helix Clients Download pages
>- Look for P4Merge (Helix Visual Merge Tool (P4Merge))
>- Dowload it and install it (C:\Program Files\Perforce)
>- Just select the merge feature and unselect the others.

9. Set P4Merge as Diff Tool Comparing
```
$ git config --global diff.tool p4merge
$ git config --global difftool.p4merge.path "c:/Program Files/Perforce/p4merge.exe"
$ git config --global difftool.prompt false
$ git config --global merge.tool p4merge
$ git config --global mergetool.p4merge.path "c:/Program Files/Perforce/p4merge.exe"
$ git config --global mergetool.prompt false
$ git config --global mergetool.keepBackup false
```
