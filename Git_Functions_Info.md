# Some useful git Functions
## Initialize and Upload all the files in a folder to github 
1. Make a new empty repository on github.com.
2. Copy paste the commands shown on screen.

### Incase you mess things up here is the commands : 

1. `git init` : Initializes the current folder to be tracked by git.
If you provided the wrong folder, type :
`rm -rf .git` : Deletes the .git file and resets `git init`, if this command doesn't work or something goes wrong then delete repo and start over.
2. `git remote add origin <repository url here>` : Connects git to your repository.
3. `git add filename or .`(means everything) : Add the files.
4. `git branch -main `: Sets your current branch to "main".
5. `git commit -m "commit-message"` : Commits the changes to git, make sure commit message are not empty.
6. `git push -u  origin main` : Uploads current files to the repository at the main branch.

## Basic functions needed for standard workflow
### Branch
Branch is an environment where code can be written or read from , it helps to divide your live code base with a testing one.
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
## Remote Repositories 
You can remotely access code from anywhere around the world by connecting to a remote repository either via the VS Code client or [web]("https://vscode.dev")
After you have made changes simply type : 
- `git fetch origin main ` : To get all the remote changes
- `git merge origin main ` :  To merge changes from local and remote repository. Note please make sure to rectify any merge conflicts to avoid data loss.
