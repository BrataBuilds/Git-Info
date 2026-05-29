# Git
Git is a version control software that allows you to track all the changes made in your project, files added / removed , contents of those files added/removed etc.

> Git was made by our lord and saviour Linus Torvalds.

Below are commonly used git commands.

## Configuring Git user and email
When using git for the first time you may get an error saying "please tell me who you are" and asks you to run some commands to configure your username and email to be shown when you are committing changes.
```bash
git config --global user.email "email@example.com"
git config --global user.name "Jane Doe"
```

This information is stored in your `.gitconfig` file in your home folder.

## Initialising a Repository
A repository is a folder that contains all the code and files you want to keep track of. You can keep these records locally on your computer or use an online hosting service like GitHub or GitLab or your private server, so that you can access your repository remotely. 

To get started on a brand new repo:

1. Make a new empty repository on github.com.
2. Copy paste the commands shown on screen.

> However if you want to upload an existing repo to Github then you may need to type in the commands manually.

### Manual method : 

1. `git init` : Initializes the current folder to be tracked by git. If you provided the wrong folder, type :
`rm -rf .git` : Deletes the .git file and resets `git init`, if this command doesn't work or something goes wrong then delete repo and start over.
2. `git remote add origin <repository-url-here>` : Connects git to your repository on github or other remote locations.
3. `git add <filename> or .`: Adds a specific file or all the files in the repo to be tracked by git.
4. `git branch -main `: Sets your current branch to "main".
5. `git commit -m "commit message"` : Commits the changes to git, make sure commit message are not empty.
6. `git push -u  origin main` : Uploads current files to the repository at the main branch.

## Saving a repo locally

- `git clone <repository-url-here>` - Allows you to download and initialize a remote repository into your local device.

## Managing changes of a repo
- `git push` : As discussed earlier, uploaded your current changes to a remote repo.
- `git fetch` :  Downloads the latest changes from the remote repository to your local machine but does not merge them into your working files.
- `git pull` : Incorporates changes from a remote repository into the current branch.

 
## Repo status and remote management
- `git status` : Tells you all the information related to untracked or modified files etc.
- `git status -s` : Makes the output of git status more concise
- `git remote -v` : Shows the remote repository connected to the local folder.
- `git remote remove origin` : Removes the existing git repo connected to the folder. Type `git remote add origin <repo-url>` to add it back.

## Branch
Branch is an environment where code can be written or read from ,it helps to divide your production code base with a testing one where you can test out features and merge them with your main branch.
Most of the production code branches are called "main" or "master". But you might find other branches called "experimental" etc.

- `git branch` : Shows a list of all branches. * next to a branch name indicates that it is currently selected.
- `git branch <branch-name>` : Creates a new branch. The new branch will have the same contents as the *main* branch.
- `git branch -d <branch_name>`: Deletes a branch locally.
- `git push origin --delete <branch_name>`: Deletes a branch remotely.

There are two commands for branching: 
1. `git checkout` : It is a legacy command used on older systems (pre-2019, v2.23), it allows you to change branches and also restore files.
2. `git switch` : It is a modern and more simpler command, and the recommended one. It is only used for switch branches.
### Switch
- `git switch <name>`: Switches to another branch.
- `git switch -c <name>` : To make a new branch and switch to it.
### Checkout
- `git checkout <name>` : Switches to another branch.
- `git checkout -b <name>` : To make a new branch and switch to it.

## .gitignore
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

If you accidentally added a file / folder that you did not want git to track,add the file to .gitignore and then type the following command.
`git rm --cached <name of file/folder`

## VS Code integration of git.
VS Code makes it easy to view and manage your git repositories by providing useful GUI tools. Ensure you have the following extensions to uplift your workflow.

1. [Github Repositories](https://marketplace.visualstudio.com/items?itemName=GitHub.remotehub) : To view and manage repos. An blue icon will appear on the bottom left left of your screen, where you can access the required menus. 
2. [gitignore](https://marketplace.visualstudio.com/items?itemName=codezombiech.gitignore): An extension for Visual Studio Code that assists you in working with .gitignore files.
3. [Gitlens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) : More advanced tools and features.

VS Code also shows an Icon beside your file to display :
- <span style ="color:yellow"> M </span> if a file is modified
- <span style ="color:green">U </span> if a file is untracked 
- <span style="color:red"> D </span> with the name strike-through if a file is removed or renamed.
lmao