# Git
Git is a version control software that allows you to track all the changes made in your project, files added / remove , contents of those files added/removed etc.

> Git was made by our lord and saviour Linus Torvalds.

Below are commonly used git commands.

## Initialize and Upload all the files in a folder to github 
1. Make a new empty repository on github.com.
2. Copy paste the commands shown on screen.

### Or type the following commands in a terminal : 

1. `git init` : Initializes the current folder to be tracked by git.
If you provided the wrong folder, type :
`rm -rf .git` : Deletes the .git file and resets `git init`, if this command doesn't work or something goes wrong then delete repo and start over.
2. `git remote add origin <repository-url-here>` : Connects git to your repository.
3. `git add filename or .`(means everything) : Add the files.
4. `git branch -main `: Sets your current branch to "main".
5. `git commit -m "commit message"` : Commits the changes to git, make sure commit message are not empty.
6. `git push -u  origin main` : Uploads current files to the repository at the main branch.


### For local project connected to a remote repo :

- `git add filename or .` : Stages the changed files, in other words choose the files to be uploaded.
- `git commit -m "commit message"` : Commits the changes to git, make sure commit message are not empty.
- `git push -u  origin main` : Uploads current files to the repository at the main branch.

- `git clone <repository-url-here>` - Allows you to download and initialize a remote repository into your local device.
- `git pull <repository-url-here>` : Incorporates changes from a remote repository into the current branch.

 
## See info about your repo
- `git status` : Tells you all the information related to untracked or modified files etc.
- `git remote -v` : Shows the remote repository connected to the local folder.

- `git remote remove origin` : Removes the existing git repo connected to the folder.


## Branch
Branch is an environment where code can be written or read from ,it helps to divide your production code base with a testing one where you can test out features and merge them with your main branch.
Most of the production code branches are called "main" or "master".

- `git checkout -b new-branch-name` : To make a new branch.
- `git branch -name `: To select an existing branch. Use the `-a` flag to show all the branches.
- `git branch -d <local-branch-name>`: Deletes the branch locally.
- `git push origin --delete <remote-branch-name>` :Deletes the remote branch.
- 

## Git Ignore
A .gitignore file is a text file used by Git to specify which files and directories should be ignored and not tracked. Useful for folders that contain libraries and modules.

```
# Comments start with a hash symbol

# Ignore files with the .pyc extension
*.py

# Ignore the "secret.txt" file
secret.txt

# Ignore the "logs" directory and its contents
logs/

```
> In VS Code you will find that the file in the explorer tab is greyed out.

## VS Code. 
You can remotely access code from anywhere around the world by connecting to a remote repository either via the VS Code client or [web]("https://vscode.dev").

Download the [remote repo extension]("https://marketplace.visualstudio.com/items?itemName=ms-vscode.remote-repositories"). Select your platform and enjoy !

VS Code also shows an Icon beside your file to display :
- <span style ="color:yellow"> M </span> if a file is modified
- <span style ="color:green">U </span> if a file is untracked 
- <span style="color:red"> D </span> with the name strike-through if a file is removed or renamed.
