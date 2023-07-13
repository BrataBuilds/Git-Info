# Some useful git Functions (I learnt)
Note to self: Use gitbash and not powershell

## Uploading all the files in a folder to github
1. Make a folder called Github and only add the files you wanna upload.
2. Make a new empty repository on github.com.
3. Copy paste the commands shown. 

## 4. Incase you mess things up here is the list of commands : 

1. `git init` : Initializes the current folder to be 'gitted'.
If you provided the wrong folder type :
`rm -rf .git` : Deletes the .git file and now you are safe (Hopefully!)
2. `git remote add origin <repository url here>` : Connect git to your repository.
3. `git add filename or .`(means everything) : Add the files.
4. `git branch -main `: Etlling Git to look at the main branch.
5. `git commit -m "commit-message"` : Commits the changes to git, commit message compulsory
6. `git push -u  origin main` : To upload current files to the repository at the main branch.

## Branch
Branch is an environemnt where code can be wrriten or read from , it helps to divide your live code base with a testing one.
Here the main code base is called "main".

- `git checkout -b new-branch-name` : To make a new branch.
- `git branch -name `: To select an existing branch.

## Remote status
- `git remote -v` : Get remote status 
- `git remote remove origin` : Removes the existing git repo connected to the folder.

## Git Ignore
A .gitignore file is a text file used by the version control system Git to specify which files and directories should be ignored and not tracked. 

```
# Comments start with a hash symbol

# Ignore files with the .pyc extension
*.pyc

# Ignore the "secret.txt" file
secret.txt

# Ignore the "logs" directory and its contents
logs/
```

In VS Code you will find that the file in the explorer tab is greyed out.

