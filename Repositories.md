# BitBucket
BitBucket is one of the few places that offers Mercurial repository hosting and also offers free plan for unlimited public or private repositories.

## Configuring the service
1. Go to https://bitbucket.org/

2. Get your local Git repository on Bitbucket
Step 1: Switch to your repository's directory
Step 2: Connect your existing repository to Bitbucket
```
$ git remote add origin https://jacesca@bitbucket.org/jacesca/git2022.git
$ git push -u origin master --tags
Enumerating objects: 86, done.
Counting objects: 100% (86/86), done.
Delta compression using up to 8 threads
Compressing objects: 100% (81/81), done.
Writing objects: 100% (86/86), 200.28 KiB | 16.69 MiB/s, done.
Total 86 (delta 42), reused 0 (delta 0), pack-reused 0
To https://bitbucket.org/jacesca/git2022.git
 * [new branch]      master -> master
 * [new tag]         v1.0 -> v1.0
branch 'master' set up to track 'origin/master'.
```

# GitHub
1. Go to https://github.compression
2. Get your local Git repository on GitHub
```
git remote add origin https://github.com/jacesca/GitCourse2022.git
git remote add origin https://github.com/jacesca/GitCourse2022.git
```

# Comparissons between BitBucket and GitHub
- Bitbucket is delimeted by private repo contributors. GitHub is delimeted by number of private repos.
- Both provide a free seervice level and allow unlimited public repositories.
- GitHub has more social or sharing features.
- BitBucket allows us to have private repositories.
- Both have repositories, branches and pull request.
- GitHub has gists and organizations. BitBucket calls them snippets and teams. GitHub has teams, but they belong a different concept. 
- Both have some type of issue tracking system. Bitbucket can be integrated with JIRA and GitHub with almost any Third Party solution.

# Generalities

## To show remote repositories on our local system
```
$ git remote -v
```

## To remove a remote repository
```
$ git remote -v
origin  https://jacesca@bitbucket.org/jacesca/git2022.git (fetch)
origin  https://jacesca@bitbucket.org/jacesca/git2022.git (push)

$ git remote rm origin
$ git remote -v
$
```

## To clone a remote repository
```
$ git clone https://github.com/jacesca/GitCourse2022.git
$ git clone https://github.com/jacesca/GitCourse2022.git demo-github 
                                  <-- This second option set an own name for the cloned repository
```

## To remove a remote repository locally
```
$ rm -rf GitCourse2022
```

## Quick Tip: How to Work with GitHub and Multiple Accounts
https://code.tutsplus.com/tutorials/quick-tip-how-to-work-with-github-and-multiple-accounts--net-22574

## Remove/Update the saved credentials:
1. Click Start
2. Search for 'Credential Manager'
3. Select 'Windows Credentials Manager' > 'Windows Credentials'
4. Search for the credentials that you want to remove/update
5. Click on the credential entry > Click 'Edit' or 'Remove'