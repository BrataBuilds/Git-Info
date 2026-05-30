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
3. `git add <filename> or -all`: Adds a specific file or all the files in the repo to be tracked by git.
4. `git branch -main `: Sets your current branch to "main".
5. `git commit -m "commit message"` : Commits the changes to git permanently, make sure commit message are not empty.
6. `git push -u  origin main` : Uploads current files to the repository at the main branch.

## Managing tracked files 
### Commannds 
One thing to note is when you add a file using `git add` it marks the file as staged, meaning git is aware of its changes but haven't made them permanent, until you run `git commit`
- `git add --all or -A` : self explanatory.
- `git add .` : Adds all the files in the current directory only.
- `git add *` : Stages new or modified files
- `git rm --cached <filename>` :  Stop tracking changes in a given file.
- `git restore <filename>` : Restores a given file to its original / last committed state.
- `git restore --staged <file>` : Removes a file from the staging area.
### .gitignore
A .gitignore file is a text file used by Git to specify which files and directories should be ignored and not tracked. Useful for folders that contain libraries and modules. It is best practice to always include a .gitignore with your project.

```
# Comments start with a hash symbol

# Ignore files with the .pyc extension
*.py

# Ignore the "secret.txt" file
secret.txt

# Ignore the "logs" directory and its contents
logs/

```
> In VS Code you will find that untracked files in the explorer tab are greyed out.



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

- `git branch -a` : Shows a list of all branches. * next to a branch name indicates that it is currently selected.
- `git branch <branch-name>` : Creates a new branch. The new branch will have the same contents as the *main* branch.
- `git branch -d <branch-name>`: Deletes a branch locally.
- `git push origin --delete <branch-name>`: Deletes a branch remotely.
- `git branch -m <old-name> <new-name>`: Rename a branch.

There are two commands for branching: 
1. `git checkout` : It is a legacy command used on older systems (pre-2019, v2.23), it allows you to change branches and also restore files.
2. `git switch` : It is a modern and more simpler command, and the recommended one. It is only used for switch branches.
3. `git restore` : It is the alternative to checkout for restoring unstaged files to their original/last committed state.
### Switch
- `git switch <name>`: Switches to another branch.
- `git switch -c <name>` : To make a new branch and switch to it.
### Checkout
- `git checkout <name>` : Switches to another branch.
- `git checkout -b <name>` : To make a new branch and switch to it.

## Merging Branches (Locally)
Merging is the process of integrating changes from one branch (e.g., your feature branch) into another (e.g., main).
he Merging Process

To merge a branch, you must always be on the branch you want to receive the changes.

1. Switch to the target branch: `git switch main`

2. Ensure it is up to date: `git pull origin main`

3. Merge the feature branch into it: `git merge <feature> -m "Merging onto main from feature or some other message` 

## Handling merge conflicts 
When running `git merge`, conflicts can occur when two branches modify the exact same lines in the same file differently, or when one branch deletes one or more files that another branch modifies.


Heres what the conflict error may look like :
```
git merge feature
Auto-merging app.py
CONFLICT (content): Merge conflict in app.py
Automatic merge failed; fix conflicts and then commit the result.
```

Check which files are affected :
```git status
both modified:   app.py
both modified:   styles.css
```
### Merge Conflict markers 
When Git cannot resolve a file automatically, it inserts markers like this:

```
<<<<<<< HEAD
current branch version code 
=======
incoming branch version code 
>>>>>>> feature-branch
```
The fix is to manually delete the <<<<<<<, =======, and >>>>>>> markers, and rewrite the code exactly how you want the final version to look (you can keep one side, the other, or combine them). Then add and commit the file normally.

### Rebase 
Rebasing is another way to integrate changes, but it rewrites history. Instead of creating a merge commit, rebasing takes the commits from your feature branch and "replays" them one by one on top of the latest main branch. It creates a perfectly linear, clean project history without the clutter of merge commits. 
>[!CAUTION]
> Never use rebase on any public branches, always use them on your own branch.
```bash
# 1. Save your uncommitted changes in your feature branch.
git add --all
git commit -m "WIP: feature"
# 2. Switch to main and pull the latest changes 
git switch main
git pull origin main
# 3. Switch to feature branch
git switch feature 
# 4. Apply rebase 
git rebase origin/main
# 5 If no conflicts occur, Push with --force-with-lease :
git push --force-with-lease origin feature/login-form
```
Git removes your commits from the branch temporarily.
Moves your branch to main’s latest commit.
Replays your commits one by one. This makes pull requests clean and free of conflicts. Because rebase rewrites history, you need to force push.
## Reverting back to previous commits
- `git revert HEAD`: Reverts back to the previous commit.
- `git revert <commit-id>`: Reverts back to a specific commit.
- `git reset` : Stop tracking all files.
- `git reset --hard <commit-id>`: his option actively deletes subsequent commits from your history, moving your branch timeline backward to the exact point you specify.
- `git reset HEAD~1`: To undo the last commit but keep your actual code changes as unstaged files.
- `git checkout <commit-id>`: This allows you see the previous commits in a read only state, to return back to present type `git checkout <branch-name>`

## Git stash
If you suddenly need to switch branches (e.g., an urgent bug fix comes in), Git will often block you from switching because your uncommitted changes conflict with the branch you want to check out. Note git stash works like a stack.
- `git stash (or git stash push)`: Takes all your uncommitted, tracked changes and shelves them. Your working directory is now clean.
- `git stash push -m "descriptive message"`: Highly recommended over the standard git stash. If you stash multiple times, having a message like "wip: fixing the navbar CSS" makes it much easier to find later.
- `git stash list`: Shows you all the stashes you currently have saved. They are indexed starting from 0 (the most recent). It looks something like this:
- `git stash pop`:
Takes the most recent stash (stash@{0}), applies the changes back to your working directory, and deletes that stash from the list.
- `git stash pop stash@{n}` : Allows you to apply a specific older stash from your list.
- `git stash apply stash@{n}`: Applies the given stash to your working directory but keeps it in the stash list. This is useful if you want to apply the same stashed changes to multiple branches.
- `git stash pop stash@{n}`: Deletes an entry of the stash without applying it.
- `git stash clear`: Removes all entries. 





## VS Code integration of git.
VS Code makes it easy to view and manage your git repositories by providing useful GUI tools. Ensure you have the following extensions to uplift your workflow.

1. [Github Repositories](https://marketplace.visualstudio.com/items?itemName=GitHub.remotehub) : To view and manage repos. An blue icon will appear on the bottom left left of your screen, where you can access the required menus. 
2. [gitignore](https://marketplace.visualstudio.com/items?itemName=codezombiech.gitignore): An extension for Visual Studio Code that assists you in working with .gitignore files.
3. [Gitlens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) : More advanced tools and features.

VS Code also shows an Icon beside your file to display :
- <span style ="color:yellow"> M </span> if a file is modified
- <span style ="color:green">U </span> if a file is untracked 
- <span style="color:red"> D </span> with the name strike-through if a file is removed or renamed.