If you are doing this first time then you will need to tell git who you are by below configuration command
````
git config --global user.name 'your name'
````
````
git config --global user.email 'your email'
````

> To change default branch name e.g. main or master
````
git config --global init.defaultbranch 'main'
```` 
> to verify all your configuration use command
````
git config --global -l
```` 
> or to view local configuration use below command
````
git config --local -l
````

> To clone existing repository to you local machine use comand
````
git clone url-of-your-git-repo [optional directory name]
````

> To initialise a git project right click on the directory and choose git bash, then verify the path is correct and apply command
````
git init
````

### SSH Key configuration
> To generate ssh key
1. open git bash from windows start menu, mac users can just use their terminal
2. open this link [generate ssh key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
3. enter below command on your git bash then press enter, don't enter any password, just hit enter (don't enter any password), enter again in confirm password
````
ssh-keygen -t ed25519 -C "your_email@example.com"
````
4. enter below command on git-bash
````
eval "$(ssh-agent -s)" 
````
5. enter below command on git-bash
````
ssh-add ~/.ssh/id_ed25519
````
6. open this link [add key to your git hub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
7. enter below command on git-bash, this command will copy your public key into your clipboard
````
clip < ~/.ssh/id_ed25519.pub
````
8. now you need to paste it into your github account, so got to settings, ssh - gpg key section, new key, give any name and paste in big box below as in second link
### Remote commands
1. To add remote or to link your local repo to remote use command below for, this generally one time command per repo.
````
git remote add origin link-to-your-git-repo
````
2. To check what is remote url in your repo use below command.
````
git remote -v
````
3. To Update remote url: command below will update your remote origin url to new-url, this is useful when you added remote with wrong remote url or you are switching to different repository
````
git remote set-url origin new-url 
````
### commit and push
````
git add .
````
````
git commit -m 'message'
````
````
git push origin name-of-branch
````
### Branching commands
1. List all branches
````
git branch
````
2. Create New Branch
   To create new branch with name `name-of-branch` from `main` do below
 ````
git checkout main 
 ````
And then
````
git checkout -b name-of-branch
````
3. Switch to another branch
````
git checkout name-of-branch
````
4. Rename a branch, to change name of branch use command from the branch, bellow command will change name of current branch so make sure you are into the branch you want to change the name. e.g. you are int branch name `task1` and you want to change its name to `new-name-of-current-branch`
````
git branch -M new-name-of-current-branch
````
To change name of branch from different branch use command e.g. you have a branch named `old-branch-name` and you want to change it to `new-branch-name` and you are currently on branch `main'
````
git branch -M old-branch-name new-branch-name
````
### Delete branch commands
1. To delete a branch from remote use command below
````
git push --delete origin name-of-branch 
````
2. To delete a branch form local use command below
````
git branch -D name-of-branch
```` 
### Synchronizing (update your local branch from remote)
1. Get changes from remote using command below
````
git fetch
```` 
2. Switch to main or master branch using command below
````
git checkout main 
````
3. Pull changes to your main or master branch
````
git pull origin main
````
#### Rebase a branch
To rebase your local branch on top of latest master or main first follow above three steps to update your master or main branch and then checkout to your local branch using command below
````
git checkout name-of-your-local-branch
````
Now use rebase command to change base of your local-branch
````
git rebase master/main name-of-your-local-branch
````
### Clean up (removing all local changes)
To remove all local changes which are not committed, and also delete any new file use git clean command below
````
git clean -f
````
### Amend
> amend command is generally used to change either commit message or add more files to last commit, below are two common options to amend

1. To add more changes to last commit without changing commit message use command below
````
git commit --amend --no-edit
````

2. To either change last commit message or add more files in last commit with option to change commit message use command below
````
git commit --amennd
````

> when amending changes which are already pushed to origin you will have to use command
````
git push -f origin branch-name
````
### reset
> Before doing any of reset task check your commit is there in list resulted by command below
````
git reflog --date=iso
````
if you see your change here you can always get it by command

````
git reset --hard "HEAD@{2022-10-30 10:19:07 +0000}"
````
Below reset command will reset and keep changes
````
git reset --soft HEAD~3 
````
Below reset command will reset your commit and discard it
````
git reset --hard HEAD~3
```` 
### Stash
1. To park changes temporary
````
git stash
````
or with meaningful message
````
git stash -m 'message'
````
2. To get temporary changes from stash, but also keep it in stash list
````
git stash apply
````
3. To get temporary changes from stash, and delete it from the stash list
````
git stash pop
````
4. To list all stash
````
git stash list
````
5. To delete last stash item
````
git stash drop
````
6. to delete all stash items
````
git stash clear
````
### squash, amend
Command below will let you squash or amend changes in last 4 commits
````
git rebase -i HEAD~4
```` 

In VI editor press `INSERT key to start editing` once edited press `ESCAPE` and at : enter wq to save or q to not save
