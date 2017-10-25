# GitHub Tutorial

_by Jessica Cai_

---
## Git vs. GitHub
### Git
* A text-based program.
* Able to control, move, and create repositories.
* A version control system that keeps snapshots of code.
* Does not rely on Github


### GitHub
* Connected to cloud9.
* A more graphic way to organize the information in a file.
* Relies on Git, to add information to the files created. 
* A platform that holds all the files.
* Tracks changes made to the file. 



---
## Initial Setup
1. First create an github account.
    * Go to github.com, create a password and username.
2. Create an cloud9 account
    * Go to c9.io, create a password and username.
3. Then open both accounts and go to your GitHub account and create an SSH key.    
    _To create an SSH key_  
    *  Go to your profile in settings and click on settings.  ![](icon.png)
    *  On the left hand side in personal settings click on SSH and GPG key. ![](GithubSSH.png)
    *  Then click on the green button that says New SSH key.  ![](CreateSSH,png)
    *  Name the title cloud9.
    *  To get the key go to your cloud9 settings.  ![](Cloud9setting.png)
    *  Click on SSH key. ![](cloud9SS.png)
    *  Copy the key that connects to your private git repository. 
    *  Go back to Github an paste this key into the place that says key.
    *  Then press Add SSH key.
    *  Lastly to make sure that everything is done right do ssh -T git@github.com, to comfirm that you have created an SSH key.


---
## Repository Setup
1. First you want to make sure that you are in the workspace directory, if you are not in the right directory then do `cd ~/workspace`.
2. Create the repository. `mkdir filename`
3. Go into the new repository made. `cd filename`
4. Initalize git. `git init`
5. Open up the file in cloud9. You can double click on the file or do `c9 filename`.
6. Make any changes to the file.
7. Then add the file to the staging area in the terminal. `git add filename`
8. Next commit the file to the staging area. `git commmit -m "type in a comment, in present tense"`
    * This takes a screenshot of the code, that you can later refer back too using `git log`.
    * You check if a file is commited or not by doing `git status`.
9. Next go to your github account and press a plus sign in the top right hand corner, and then click on make a _New Repository_.
10. Then make the new repositorys name the same name as what you named it in your cloud9 and click on the button create repository.
    * If you are asked to verify by email do it.
    * After this step, the next page will show a quick setup, make sure you are on the SSH key and not on HTTPS. You can copy the two lines of code in the section it says to "...or push an existing repository from the command line" and paste that in the cloud9 terminal. Then refresh the github page. (Steps explained further on the last step.)
11. Lastly, go back to your cloud9 and create a connection between your remote and local repo, so you can push your file to your github account.
    * First create a connection between your remote and local repo.
        * `git add remote origin URL` / _change URL to your github repo URL_
            * **git** = git command. **add** = add remote repo. **origin** = gives it a nickname. **URL** = Link to the place you are making the connection too. 
    * Next tell the computer where to push the commits
        * `git push -u origin master`
            * **git** = git command. **push** = that sends commits to the remote repo. **origin** = the remote where you send the commits. **master** = main branch. **-u** = upstream, saves the origin and master, so next time you can just do `git push`.


---
## Workflow & Commands
#### Git Commands
`git add filename` = Deciding what specific files you what to add to the staging area to be committed.  

`git add .` = Adds everything in a folder to the staging area to be committed.  

`git add --all` = Adds all changes, including deleted files, to the staging area.  

`git push` = Sends your commits to the remote repo.

`git pull` = Brings down the changes from the remote repo to the local repo.

`git commit -m "type in a message (present tense)"` = Takes a snapshot of the file and puts in the staging area.   

`git log` = Sees all past commits
    * To get out of `git log` you can press Q for quit.   
        _* Note: ^ means control_  
        
`git status` = To see which files in the staging area is ready to be committed.   

`git diff` = Shows previous snapshots of your code and your current code.  

`rm -rf .git` = To undo git init, by deleting the folder.  

#### General Commands
`pwd` = Prints working directory, lists all the content of the directory you are currently in.  

`ls` = Lists all directories and files of the directory you are in.  
`cd` = Changes the directory you are in.  

`mkdir` = Makes new directory.  

`rmdir` = Delete empty directory.   

`rm -rf` = Deletes a non-empty directory. -rf means that it will continue to delete with force nonstop until everything is gone, permanently.  

`mv`(_rename_) = Renames a file by putting it’s old name as the first argument and the new name as the second argument.  

`mv`(_move_) = Moves a file from one directory to another. Can move one or multiple sources. To move one or multiple sources the first argument is the sources names and the second argument is the destination.


---
## Rolling Back Changes
`git checkout -- filename` = To undo an edit. (_Can be found when you type git status._)

`git reset HEAD filename` = To undo an add by removing something from the staging area. (_Can be found when you type git status._)

`git reset --soft HEAD~` = To undo a commit. (_Search on google git undo commit. This command can be found on the stackoverflow website._)

`git reset HEAD~` = To undo a add and a commit. (_This command can be found on stackoverflow, in the same place where the git reset  --soft HEAD~ command can be found._)

`git reset --hard HEAD~` = To undo an edit, an add, and an commit. (_This command can be found on stackoverflow, in the same place where the git reset --soft HEAD~ command can be found._)

`git revert sha numbers (a,b,c)` = To undo commits that have already been pushed. It goes back to the previous commit. 
* To get the sha numbers, you must first do `git log`.
* (a,b,c) = a - most recent commit, b - the commit before them, c - the third recent commit 


## Collaboration
#### Cloning
`git clone URL` = Make a copy of someone else's repository.
* It can make a copy of someone elses remote repository, that way you have their remote repository on your local. However, you will not be able to push or pull anything from that repository because you do not have the owners permission. It is not your repository. 

### Forking 
* It will make a copy of someone else's remote repository, but the copy made will now become apart of your own remote repository. Then you will clone the repository that is now in your remote to your local. This way you can push or pull from the repository because it is your own repository. 
* _You can fork your own repositories._
* `git remote -v` = can help you see which remote repos are in your local repo. (_You will see a nickname and a URL_)
    * `-v` = _verbose_ 

### Pull Requests
1. First fork someone else's repository.
2. Then clone the repo you made a copy of into your local. `git clone URL` (_The URL is on github, there is a green button that says clone or download._)
3. Next make some changes to the file in the repository. Add, commit, and push those changes.
4. Go back to github and find the button that says _New pull request._ Click on it.
5. Then click on a green button called _Create pull request._ Afterwards you will see this button again, click it again. 
6. You have just sent your request to the owner of the repository, now you just wait to see if they accept your request or not.
    * If you do accept other peoples request you can use `git pull`, to see the changes they have made to your repository.















