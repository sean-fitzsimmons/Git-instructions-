# Git tutorial for bigginers: learn Git ina 1 hour YOUTUBE 
## What is git? 
Most popular version control system in the world 
    It records changes made to the code over time in a Data base called 
    a repository
    It shows who made changes and what and if mess up you can revert back to an earlier state 
Without a verison control system would constantly have to upload new infor to various folders 
Track history and work together is the plus of version control system 

### Centralized systme 
All team members connect to a cental server to get the latest copy of the code and share changes with others
    subersion and team foundation server are examples 
    problem is if the server goes off line then everyone goes down 
### Distribued system 
Every team member has a copy of the project and the history on their machines 
    Git and Mercurrial  
    90% of companies use git 

## Using git 
the command line 
    faster and easier, superior method 
    gui tools have limitations 
    gui tools are not always avaible 
code editors and ides
    vs code git lens
graphical user interface 
    git kracken and source tree 

## Configuring git settings 
1: git config --global user.name "" 
2: git config --global user.email 
3: git config --global core.editor "code --wait"
    git config --global -e
        This will open up git settings in main editor 
4: git config --global core.autocrlf true (for windows) input (for mac) 
    This is going to edit the default the end of line so it will 
    make it tranferable for a mac user and update on windows when code is pulled from the repsoitory. 
        press q to exit in the command line 
    Git config -h will give a shorter directory 
## Creating snapshots 
    These are checkpoints for you code. Should be makeing these 6-8 times a day. 
## Initalizing a repository 
mkdir Mood 
    This makes a directory inside the folder (file)
cd Moon 
    This opens up the Moon depo 
git init 
    Initializes and empty repsoitory 
    Inside the directory is .git this is a hidden file that tracks all of the files and everything we work with 
ls 
    Wont show anything 
ls -a 
    Will show .git sub directory 
start .git 
    To open .git repository 
    If you corrupt or remove this you lose your project 
## Git worlk flow 
Git work directory-> staging area-> Git respository. 
    The respository is just a .git subdirectory inside out working directory.
Commit is like taking a snapshot 
The snapshot will get perminatly stored in the respitory 
The staging area allows us to review work before commitng to the respository or take the snapshot 
Each commit contains an ID, message, date/time, and author 
## Staging files 
git init 
git add file2.txt
    This will add the file you choose to the staging area
git add *.txt 
    will add on the files with .txt endings 
git add . 
    will add everything from the directory

echo hello > file1.txt
echo hello > file2.txt 
    echo is not a git command. It only writes content into a file. These created 2 files
git status 
    This will show you the working directory.
    red means they are not in the stage area yet 
git add file1.txt file2.txt 
    This will add the files to the staging area 
    The files will be green, This indicates they are in the staging area 

echo world >> file1.txt 
    This is adding the word world to the file1
git status 
    It will show the two green files in the staged area
        and the modified file red in the working directory 
git add file1.txt 
    This will update the file in the staging area. 
    
    Real life senerio, we put a js file in the staging area, change it, then have to re add it to the staging area to change it there. 
## Commiting
git commit -m "inital commit." 
    -m means message 
    we have to type a meaningful message with the code for coworkers. 
git commit 
    if you neeed to write more then small message. 
    It will open up default code editor and first line write a small message 
    (line break)
    Write a long message and explain yourself 
## Commting best practices 
    commits not to big or too small. 
    commit about every 6-10 times a day. Just depends on what you are doing that day. 
If you fix a bug and find a type on. 
    Commit them indivdually not at the same time. 
Make meaningful commit messages 
    Make them present 
        "Fix the bug" not "Fixed the bug" 
## Skipping the staging area 
echo text >> file1.txt 
git commit -a -m "message here" 
or 
git commit -am "message here" 
    This will skip the staging area 
## Removing files 
rm file2.txt 
git status 
    removed form working direcctory but still in staging area 
git ls-files 
    This will show what is in the staging area 
git add file2.txt 
    Now that you added this, it will delete from the staging area.
git commit -m "remove unused code." 
    Now the updated snapshot with file removed is in the repository 
FASTER 
git rm file2.txt
    This will remove from working directory and staging area 
## Renaming or Moving Files 
mv file1.txt main.js
    this changes the name of the file in the working directory
git status 
    Will show that file1.txt is deleted and main.js is unstaged in red 
git add file.txt 
    This will delete the old file name from the staging area 
git add main.js 
    This will rename it to the staging area 
FASTER
git mv main.js file1.js 
    This will rename in the wokring directory and stagging area 
git commit -m "Refactor code."
## Ignoring files 
We should tell git to ignore certin files 
    log files

mkdir logs 
    Make a new directory
echo hello > logs/dev.log
    Add txt and subdirectory

echo log/ > .gitignore 
code .gitignore 
    Now this opens up a directory that we will can store as many files as we want thier 
Im pretty sure that will block all files with .gitignore 
git rm -h 
    will bring up the options you might need.
git rm --cached -r whatever.file  
    will only remove from the index
    index is the old word for stage area 
github.com/github/gitignore
    they have diferent templates for gitignore for different coding languages. 
        There are parts of different languages you do not need. 
## short status 
git status -s 
echo sky >> file1.js 
    appending the sky to the js file 
echo sky > file2.js
    Adding a new file 
git status -s 
 M file1.js
?? file2.js 
    The first column is the staging and second is the working directory. Thats why the M is only on the column 
    So the m and ?? are red. THe m is modified and ?? is not in staging area. 
git add file1.js 
git status -s 
M file1.js
    This will show green M in the left column which means it is staged
echo ocean >> file1.js 
git status -s 
MM file1.js 
    This shows that there is a modified version in the staged area and a modified version in the working directory 
git add file1.js 
git status -s
M file1.js 
    Now it shows that everything is uptodate in the staging area 
git add file2.js 
git status -s 
A file2.js 
    The A in the left column shows that the file is added 
## View staged and unstaged changes 
Always review what you have in the stating area before making a commit 
git diff --staged 
    Show what is in the staging area 
--- changes to the old coppy 
+++ changes tot he new copy 
@@ -1,3 +1,5 
    This means old copy starting at line one has 3 changes and new copy at line 1 has 5 changes 
And then show what has changed 
git diff 
    This will compre the working area to the staging area 
## Visual Diff Tools 
KDiff3
pP4Merge
WinMerge (Windows Only)
VSCode

git config --global diff.tool vscode 
git config --global diff.tool.vscode.cmd "code --wait --diff $LOCAL $REMOTE" 
    This is going to allow me to view what has changed in vs code for the staging area 
git difftool --staged 
    This will show what is in the old commit and what is in the staging area bout to go in (on the right) 
Not really used that much because most editors allow viewing of the staged and unstaged insidet the coding envirement
    To be learned later 
## Viewing history 
git log 
    Show all the commits 
    (head -> master) Main branch 
        Head is a reference to a current branch 
q 
This will quite the log 
git log --oneline 
    This will give a sumery of the commits with the messages and abreviated id 
git log --oneline --reverse 
    This will do the same thing but show the newest at the top and oldest at the bottom 
## Viewing a commit 
git show ed479ee 
    or 
git show HEAD~1
    This method will start at the HEAD commit and move down the line however many spaces 
git show HEAD~2:.gitignore 
    This will open up exactly what is commited in the terminal 
git ls=tree hEAD~1
    List all the files in the tree 
    files are represented using blob 
    and directorys by useing trees 
Git objects: 
commits, blobs(files), trees(Directories), tags 
## Unstaging Files
git restore --staged file1.js 
    list multipe files, us patters or . to restore the whole stagging area 
git status -s 
## Discarding local changes 
git restore file1.js 
    Git will take a copy of the previous version in the stagging enveriment and copy  it to the working directory 
    git restore . 
        Will replace all untracked files 
git clean 
    This is a powerful code, -h will give us all the options
git clean -f 
    This is git clean force and this will force git to get rid of any ?? untracked files in the working directory 
## Restoring a file to an Earlier version 
Deleted a file and commited it 
    oh no.. but wait 

git log --oneline 
    find the file you want to restore to 
git restore --source=HEAD~1 file1.js 
## Creating snapshot with VSCode 
go into source control
pick your file and then click the plus icone
    should give you a green A saying its stagged 
to unstag just hit the minus where that plus was 
To see what has been commited, got to the timeline drop down on the explore page 
## Creating snapshots with GitKraken 
GitKraken is a gui, its really nice to make everything easy to look at. 

## Browsing history 
git log --oneline --stat 
    This will show you all the lines there were changed in this commit 
git log --stat 
    show a little more indepth
        q to esc 
git log --oneline --patch 
    This will show the actual changes in each commit 

## Filter history 
Fiter by auther, date, content, so on 
git log --oneline --auther="authers name" 
git log --oneline --after="2020-08-17"
git log --oneline --grep="GUI"
    This is if you want to search by keyword 
git log --oneline --S"hello()"
    Added or removed a function decloration 
git log --oneline toc.txt 
    This will filter by file 
git log --oneline -- toc.txt 
    This does the sname thing.. sometimes git makes you use it 
git log --oneline --patch --toc.txt
    To use the patch option, it has to come before the files 
## formating the log output 
git log --pretty=format:"" 
    %an (auther name)
    Basically this will give you what every information you want in a super orderly fashion 
    customize the log command however you want 
## Creating Aliases 

    set up aliases for commands used frequently 
git config --global alias.lg "log --pretty=format:'%an commited %h'"
git config --global -e
    Will open up our config settings sheet in vscode to see what changes has happended 
git config lg 
    Will now run that long command up top 
one more 
git config --global alias.unstage "restore --staged ." 
    This is going to unstage everything in the stagging area. 
## Viewing a commit 
git show HEAD~2
    This will show two commits back from the head file 
git show HEAD~2:sections/creating-snapshots/staging-changes.txt 
    This will show the final version of the file stored in the commit 
git show HEAD~2 --name-only
    shows only the add, modified or deleted 
## Deleting a commit 
git reset --soft HEAD~1
    this is going to move the head to the commit just before and move the current file inot the staging area. 
git reset --hard HEAD~1
    This will move the head to the last commit and delete current file. 
## Viewing the changes across commits 
    so multiple commits 
git diff HEAD~2 HEAD
    this will show us all the commits from head 2 to head one 
git diff HEAD~2 HEAD audience.txt 
    will show the changes to a particular file 
git diff HEAD~2 HEAD--name-only
    give only the name 
git diff HEAD~2 HEAD--name-status
    to show the status of each of the commits by name 
## Checking out a commit 
    See the complete snapchat of our project at any given time. 
    It restore the working directory to a previous commit. 
        This would be great if the commit down the road is messed up and need to start from an earlier point. 
    git lg 
        to get the --oneline log of the commits
        copy the id 
    git checkout fb0d184
        This is going to detach the head from the master branch, this means i should not commit anything because it will be a dead commit.
            This is only used for viewing 
    git log --oneline --all or git lg --all
    to see all of files again 
    and to get back to the master branch 
    git checkout master 
        attaches the head to the master branch 

## Find bugs using bisect 
quickly find the bug 
git bisect start 
    tell the command that the current commit is a bad commit 
    nd go to a commit that is good and let it know what is good 
git bisect bad 
    This is telling git that the lastest commit is bad ]
git bisect good commit id 
    This is letting git know that this commit is goood so the problem is somewhere inbetween 
git log --oneline --all 
    this will show whats good and whats bad and where the head is at 
SO now the head in in the center of the commit log. and our middle commit is in the working directory, now we can run it and see if the issue is still present.
    If you commit is good, then it was in the top half of commits if it was bad then it was in the bottom half 
git bisect good 
    If it is good 
git log -oneline -all 
    Now we check where the head is again! basically it cuts our search time inhalf 
finally at the end, the head will be on the bad commit 
git bisect bad
    To tell git it is a bad commit 
    Now git knows and will present us with a snapchot from the log
gig bisect reset
    Now the interigation is over and the head is back on the master branch. 
## Finding contributers using shortlog 
    Find all the poeple who contributed to the project 
git shortlog 
git shortlog --before"" --affter="" 
    We can use these operators to view the contributors for a given date range 
## Viewing the file history 
git log toc.txt 
git log --oneline toc.txt 
git log --oneline --stat toc.txt 
## Restoring a Deleted file 
git rm toc.txt 
    Remove file
git commit -m "remove toc.txt"
    commit the changes 
To restore file 
git log --oneline -- toc.txt 
    this will bring up the log of commits to this file 
git checkout a642e12 toc.txt 
    a642e12 is the parent commit to the removed one 
git status -s 
    run a short status 
    This will show that file in the staging area 
git commit -m "Restore toc.txt" 
    The commit is restored! 
## Finding The Author of Line Using Blame 
git blame audience.txt 
    This will bring up the file who did it and the date 
git blame -e audience.txt 
    This will bring up the email too 
git blame -e -L 1,3 audience.txt 
    This will show only the first three lines 
## Tagging 
bookmarking certain parts of the project 
git tag tagname fileid 
    this will set the tag to the file 
git tag -a v1.1 -m "message" 
    You can assossiate a message with the tag 
    These are preferd over soft tags 
git tag -n 
    Will show the message 
git tag -d tagname 
    this will delete the tagname 
## Viewing browsing history on vs code 
Using an extention called gitles
    In the left bar of the editor 
we can do a lot of the function of what we want to do in the git command line but in this editor. 
    Its pretty cool 
It does not do bisect 

This is really helpful to see exactly how code is modified from one file to another but the best course of action is to use the command line 
shift ctrl p will create, delete or push tags 
add a tag for a earlier commit, find it, right click and select create tag 
## What ar barnaches 
    A seporated isolated workspace 
    Different from the master branch where you can work on unstable code, then when you are ready, merg it to the master code 
Git manages branches different 
Git tracks what branch currently on by using head 
## Working with branches 
    We just got a bug report and have to make a new branch 
git branch bugfix
    making a new branch called bugfix 
git branch 
    This will show the brnaches
git status  
    Will show what branch i are are
git switch bugfix 
    Switch between branches 
git branch -m bugfix bugfix/signup-form 
    this changes the name 
code audience.txt
    opened up and changes made
git log --oneline 
    This shows that the head is on the bug branch but i can still see the the master branch and all of those past commits 

If i switch back to the master branch then i can see the old version of the adiuence.txt, so different branches allow for working in isolation 

git log --oneline
    Doing this in the master branch i can not see the commits done in the bug branch 
git log --oneline --all
    This will view the commits across all branches 
### Deleteing a branch 
git branch -d bugfix/signup-form 
    Can not delete the branch until it is fully merged with the master branch 
git branch -D bugfix/signup-form 
    This capital D will do a force delete 
## Comparing Branches 
Show how the branches are diverging from the master branch 
got log master..bugfix/signup-form 
    RThis will show the commit and auther 
git diff master..bugfix/signup-form 
    This will show the changes made in the new branch 
or

git diff bugfix/signup-form 
    Does the same thing 
git diff --name-status bugfix/signup-form 
    This will bring up the name of the file changed and where it is at in the staging area 
## Stashing 
if you are on a branch and then stage a some changes, then need to switch over to another branch you either have to commit the changes or stash them. If you do not they will be deleted. 

Stashing in the git repository
stage the file 
git stash push -m "meaningful message" 
    This will save it to the working directory and index state on master. 
git stash push -am "meaningful message" 
    This will save more stuff in stash 
git stash list 
    This will show what is stashed 
git stash show 0
    Show information on the stash what was changed and what the file is starting at 0  
git stash apply 0
    Apply the changes in stash to the working directory 
git stash drop 0 
    get rid of the stash 
git stash clear 
    reomve all stashes 
## Merging 
bringing changes from one branch to another 
Fast-forward (if branches have not diverged)
3-way (if branches have diverged)
## Fast-forward Merges 
git log --oneline --all --graph 
    This will give a better representation of the branches 
    Change this motherfucker in to a shortcut.. its too long 
So to do this, the master has to be behind the new branch you want to merge. This means it is in the same line.
    If you commit to the master after the new branch, then you have to use the three-way method
Make sure to delete the old branch after merged 
### switch and create a new branch short cut 
    git switch -C bugfix/login-form
### Merge with no fast-forword option 
    git merge --no--ff bugfix/login-form 
        This will open up the editor and generate a message describing what happend 
    change the message or close the file 

    merge commits are harder to read and pollutes the history.
    Some people like just a linear history 

    Allow reverting a feature easier 
    plus side is its a true reflextion of the history 

### Disabling fast-forward merging 
    git config ff no 
        This will disable fastforward in the current respitory 
## 3-way Merges 
Useful when having havinga branch that is diverging commits 
Its going to work just like no fastforward commit, opening up the file and renaming it. 
## Viewing the merged branches 
git branch --merged 
    This shows all of the branched merged with the master 
For good paractice, delete all of the branches 
git branch --no-merged 
    This will show all the branches that have not been merged 

## Merged Conlficts 
git merge branchname 
    a conflixt message is going to come up and open a file in the editor 
git status 
    This will show you what files have the confilct 
You can accept the master change, accept the other change or accept both. 
You can manually take away the stuff git added to show the difference with the merges. 
DO NOT add anything new 
    its called an evil commit 
git add filename
git status 
    This will tell you if your confict is fixed 
git commit 
    accept the default message 

## Merging tools 
kdiff
p4Merge 
winMerge(windows only)

## Aborting a Merge 
git merge --abort 
    This will take back to the state before the merge
## Undoing a faulty merge 
1: is to remove the commit like it was never there 
be careful
if shared commits with other team members or pushed it to a repository 
2: Revert the commit 
    create a new commit that will cancel all the changes in this commit 
    soft: 
        put the head on the last commit 
    mixed: 
        put the head on last commit and put the reset commit in the staging area, local changes in the directory are not effected 
    hard: 
        Git is going to take the snapshot and put it in the working directory too 
            This is the state we were in before starting the merge 
git reset --hard HEAD~1
    This is going to take us back to the point before initiating the merge 
Last commit id : 4530f6f 
    Take a copy of this if need to revert the reset        
git reset --hard 4530f6f 
    This will take us back to the merge commit we just reste 
        This is possible because the commit was stored in the git repostiory 
** If we has shared the history to coworkers or the repsoitory, instead of undoing, hhave to revert the last commit 
git revert -m 1 HEAD 
    We have to revert to the last commit in the master branch before starting the merge 
    -m 1 means 




## Squash Merging 
This is basically a way to turn a 3 way merge into a linear commit history. 
Only use this on small short lived branches. 

git merge --squash bugfix/photo-upload 
    This is going to take all of the contents of the branch and put them into the stagging area of the master branch to be commited 

git branch -D bugfix/photo-upload 
    Make sure to delete the bugfix branch because it will not be seen as a merge and cause problems and clutter down the road

May get some conflicts using this method, the process to solve is the same 
## Rebasing 
Bringing changes from one branch to another 
Change the base of a branch to the current master branch, to create a direct linear path 

This rewrites history so only use it for local changes, not if you have shared with people on the team or pushed 
git switch feature/shopping-cart 
    switch to target branch 
git rebase master 
    telling git to rebase the branch to the last commit on master 
    Most of the time when you rebase you end up with conflicts 
git log --oneline --all --graph
    Now have a direct linear branch of feature branch to master 
git switch master 
git merge feature/shopping-cart 
    No this will be a fastforword merge 
git branch -D feature/shopping-cart 
    Delete the old branch. 
### encountering conflict during rebasing 
solve as normal 
git rebase --continue
    This will keep the it going 
git rebase ---skip 
    If you get a lot of conficts and really do not are about that commit that much. 

## Cherry picking 
cherry pick a particular commit and put it on master instead of merging the whole branch 
git cherry-pick 10f08dc 
    Us the commit id of the commit you want to cherry pick to the master 
If you do not delete the branch and then try to merge the whole thing in the future, conflicts are going to happen 

## Picking a file from another branch 
git restore --source=feature/send-email toc.txt
 or 
git restore --source=feature/send-email -- toc.txt
    This will bring the commit from the selected branch into the working directory of the branch currently in 
cat toc.txt 
    show the changes 

## Working with branches in VSCode 
    use gitLens 

# Collaboration 
How to work with others!!!
## Workflows 
centrilized work flow 
    a shared repsotiory everyone can sync up to 
        some use private server or a cloud 
Interation-manager 
    main repsoitory 
    maintainer 
    constributers 
        A fork is made of the main repsoitry and the contributers put a copy of that on there device 
        They then make commits and push to the copy repsoitry and send a pull request to the maintainer
        the maintaier pulls the commits from the copy repo and makes sure its good 
        if it is, they push it up to the real repo. 
## creating a git hub repository
    go to drop down, new repo 
    public
        private costs money
    pick a fist commit 
    the master branch is now called main in github 
## Adding contributers 
No one can push to the gh repo 
    You have to give people access 
Go to settings in the repo 
    manage access 
        invite collaberator 
            This will send them an email 
            once they accept then they will have push access 
## Cloning a Repository 
Everyone should clone the repsitory 
go to clone tab in git hub 

git clone https://github.com/sean-fitzsimmons/Git-course.git gitcourse 
    give it a name at the end 
    This clones the repsoiory on my local device 
Main is master 
    orgin/main is a remote tracking branch 
    orgin/HEAD tells us where the head is in the working repository 
git remote
    will bring up origin 
git remote -v 
    Will bring up the path to the repsoitory in github(url); 
## Fetching 
    MAIN = MASTER 
If new commits are made to the remote respoitory, the local will not know 
    git fetch will a download the new commis and set the origin/MASTER to the new commits. 
It will not move the master in the local repository 

git fetch 
    This will assume want to fetch the commits from origin 
        git fetch origin branchname 
            To fetch from different branches 
    This will download the new commits in the remote repo to my local repo 
git merge origin/master 
    This will merger local branch to the origin/MASTER on the local machine, bringing the whole project up to date. 
        May experience some conflicts 
git branch -vv 
    shows how the local and remote branches are diverging 
git merge origin/main 
    fastforward merge 
git log --oneline --all --graph 
    
    (HEAD-> main, origin/main, origin/HEAD) 
        means everything is merged and the master is up to date. 
git branch -vv 
    shows main and origin are snyced up 
## Pulling 
Pull combines fetching and merge 
git pull
    This is going to make a three way merge
git pull --rebase 
    Puts the new local commit ahead of the new remote commits making a lineral log 
the (HEAD-> main) wont be synced up in a row like the fetch/merge method because we made a new commit in the local repo as well...
Everything will sync up when i push our local commit to the remote commit!
giving the (HEAD-> main, origin/main, origin/HEAD) 

## pushing 
    MAIN = MASTER lesson is older.
Now that we have pulled the info from the remote, we have a new commit in the local that can be pushed up to the remote, syncing them up
    currently the local main branch is one head of the origin/main 

git push origin main 
or 
git push
    if on the main brach git will use that 
    git will also assume origin 
        can just use git push 
Now the remote and local are all synced up!!

If git push does not work then someone might of just pushed onto the remote, do a pull request and then push after conflicts are resolved. 

NEVER USE git push -f 
    This will delete the other persons code and replace yours. 
## Storing credentials 
git config --global credential.helper cache 
        will store credential for 15 minutes 
git credential-osxkeychain 
    install
git config -- global crdential.helper oxckeychain
    This will do it perminatly, basically wont have to put in cridentals when you push 

I did have to put in any when i pushed this last time so lets see if they updated this feature or i need to add all this 

Git-Credental-Manager-for-Windows 
    on git hub to install it 

## Sharing tags 
By defalut the push comand does not trasfer tags to the remote repo 
    Have to explicitly tell it to 
git push origin v1.0 
    this sill push the tag 
git push origin --delete v1.0
    This will delete the tag 
    Now the tag is gon on git hub 
git log --oneline 
    The tag is still in the local 
git tag -d v1.0
    Now it is fully deleted 

## Releases 
Create a release to package files, source code or whatever. Basically a place that has notes a file you want to publish as a release 
go to tags 
create new release 
## Sharing Branches 
Share branches with team members they must be explicetly sent 
git switch -C feature/change-password 
    make a new branch 
git branch -vv 
    This will show all of the local branches 
git branch -r 
    shows all of the remote tracking branches 
git push -u origin feature/change-password 
    this will push the branch up. -u is a shortcut for push upstream 
    because we can not just use git push for a branch 
        Now can use this branch like using the master 
git push -d origin feature/change-password 
    Deletes it from the remote repo 
git branch -vv 
    But it is still in the local repo 
git switch main 
git branch -d feature/change-password 
    Delete the branch off the local repo 
## Colaberation workflow 
    Working with a team member cinero 
        Start by making a branch.
            Easiest to just make one in the remote repo 
    As we push to this branch, can see how far it is ahead of master 
git fetch 
    This will show what branches are in the remote 
git branch 
    Ionly shows main
git branch -r 
    shows that when using fetch got a remote tracking branch
    Now should make a local branch that maps to this repo 
git swithc -C feature/change-password origin/feature/change-password 
    This wil switch to a new branch and set up to track the remote branch with he same name. 
My team member Amy
    She is going to go onto the repo and copy the url 
git clone https.url-righthere.git 
    This will tell you what repo it was cloned into 
cd thatrepename 
git switch -C feature/change-password origin/feature/change-password
    Now amy has the right branch and set up tracking to the remote branch of the same name 
Amy and i are going to keep pushing to the branch and pulling eachothers changes and resolving conflicts, resolve them and then do another push 

At some point this feature will be complete and we have to merge it to the main branch 

git pull 
git log --oneline --all --graph 
    My feature is one branch ahead of master 
        Need to merge 
git switch main 
git merge feature/change-password 
    Now main is pointing to the newest commit 
git push 
    To push the merge up to the remote repo 
git log --oneline --all --graph 
    main, origin/main are lined up.     
    In remote repo we have 5 commits 
git push -d origin feature/change-password 
    This will remove the branch from origin and remote repo 
git branch -d feature/change-password 
    This will remove it from the local repo 

Amy needs to do after 
git switch main 
git pull 
    Take the changes from the remote to her local device
git branch -d feature/change-password
    removes from the local branch 
git branch -r 
    The feature remote tracking branch is still there 
git remote prune origin
    This will get rid of the tracking branches no longer in use 
Now amy is all up to date and we can go back to making some badass stuffs 

## Pull requests
Get other team members opinion about code. 
Amy is back. She is going to make a new branch, add a commit and then add it to github
amy used 
git switch -C feature/login 
    Creating a new branch local 
echo hello > file3.txt 
    create a new file 
git add . 
    add to the staging area 
git commt -m "write hellow to file" 
    Commits the message 
git push -u origin feature/login 
    -u needs to be used when pushing a new branch to the remote repo for the first time. This creates a remote branch in the repo. 
        Does not need it every time tho, just for a new branch from the local so this is super werid 
A pull request is basically just a way to compare two branches on 
  use compare and pull request button on github 
    Pick two branches, one to merge into and the one merging 
        It will tell you if it able to merge or if there are conflicts 
    Add a reviewer from the colaberaters on the project 
        This will send them an emial and request they review the merge 
The reviewer: 
    They will see one open pull request in github on the pull request button 
    Can see all of the changes in the code and you can add invidual notes to each line 
    Hit finish review
        write a general description 
The Pull Requester: 
    Now amy make changes, pushes them up to the remote repo
    request the reviewer once more 
The reviewer: 
    Sumbit the file review and leave a comment 
The pull requester: 
    WIll see a checkmark by the reviewer and can go ahead with the merge 
        Some companies beleive whever started the pull request should end it, some think if you started it you should not end it because it defeats the purpose of the request 
git switch main 
git pull 
    Get the new local up to date with the remote repo 
git log --oneline --all --graph 
    Everything is up to date
git branch -d feature/new 
    Delete the branch 
git branch -r
    Check if remote tracking branch is still running
git push -origin --delete Feature/new 
    This will remove the remote tracking branch 

## resolving conflict 
    It is a very similar to resolving conlficts on in the git terminal, you can just use the github interface to resolve them too. And when its all good just merge it on into the master!

## Issues 
Issue tracking goes hand and hand with pull request 
    Issue tab of github will track bugfixes enhancments and any other type of issure want to track witht the team 
Attach file and leave a comment so that all issues are in one place.
    Can assign issues to more then one people. 
    Or people can come in and assign issues to themselves 
Add labels to the issue 
    bug, documentation, duplicate, enhancment, etc.
Link to pull request so when pull request are open and closed, it will close the issue as well.
    can always come in and close the issue manually 
## How to customize labels
Go to issues then Labels 
    new label 
        name, desciptin, and color
            Create label 
    In labels we can see what is open or using that label
        Organize the issues by label basically. 
## Milestones 
Use milestones to track the progress of various issues 
    Select certain issues and place them in a milesstone
        This will help to keep eveything organized
    One issue have been assigned to milestones, if we close the issue it will mark the milestones complete. 
        If you have mulitple issues to the milestone then it will take multiple issues closing to complete the milestone 
## Contributing to open-souce projects
When you do not have push access to an remote repo
    Fork, 
        Fork is going to make a complete copy of the repo on your account   
            You can pull, push and do whatever you want on this fork copy. 
    Clone the account and add it to your local  
        ready to go! 
Forked a old repo form mosh
git clone https://github.com/sean-fitzsimmons/codewithmosh.git
    This clones to the local repo 
cd codewithmosh 
    This puts us in the repo 
git switch -C bugfix 
    make and switch to new branch called bugfix 
echo hello > README.md
    Put hello to read me 
git commit -am "update read me" 
git log --oneline --all --graph 
    check out if everything went in correctly 
git push -u origin bugfix 
        -u because first push this new branch 
            origin represents fork repo 
                bugfix, the name of the newbranch to be pushed 
When opening a pull request it is going to first compare to the main branch that you forked repo off. 
    You can just merge to your own fork but the default is the main repo that you forked. 
git swwitch master 
git branch -d bugfix
    Delete local branch 
git branch -r 
    See what tracking branches still open 
git push --delete origin bugfix 
    This delete the tracking branch 

## Navigate files in bash 
bash file navigation 
    cd ~/Desktop/Git-course 
        put the desktop the repo name
## Keeping a forked repo up to date 
    Have a refernce to the forked repo using origin 
        add anther reference called base,
            The base is the original repo 
                we can pull from the original repo to the local and then push the updated info to your origin repo 
git remote
    Tells us what the remote refernce we have.. will say origin
git remote -v 
    Shows the exact chanel url of the reference repo 
git remote add upstream theurlofthebasecode.com 
git remote 
    This will say origin and upstream 
git remote rename upstream base 
    This rename upstream to base 
git remote rm base
    This will remove it 

Some code got changed in the base code 
git fetch base 
    This will get the new code form the base repo
git switch master 
    Switch over to the main branch 
git merge base/main 
    Now the local repo is insync witht he base repo 
git push 
    This will automaticlly push to the origin 

Its good practice to merge master branch to the local branch becasue it will reduce conficts in the future 

AND NOW YOU ARE UP TO DATE!

## Why rewrite history 
    Why we need histery? 
        To see what was changed, why and when. 
    Bad history 
        Poor commit messges 
        large commits 
        small commits 
    Clean history 
        Shows the story of our project 
    Tools to clean 
        Squash small, related commits 
        Split large commits 
        Reword commit messages 
        Drop unwanted commits 
        Modify content of commits 
    VERY DANGEROUS 
        Need to know what you are doing before touching the history 
## The golden rule of rewriting history 
DON'T REWRITE PUBLIC HISTORY 
    It just makes thh history supernoisy and not linear 
    Once you push your work, its pubic and final 
Always clean up private history before sharing with world

## Example of bad history 
* 088455d (HEAD -> master) .
    This just has a period 
* f666091 WIP
* 111bd75 Update terms of service and Google Map SDK version.
    This should be split into two different commits, Update term of service has nothing to do with Google Map SDK version
* 72856ea WIP
    Work in process commits are just noisey history 
* 8441b05 Add a reference to Google Map SDK.
    This should be before render restrants on the map 
* 8527033 Change the color of restaurant icons.
    This, fix a typo and render can all be together
* af26a96 Fix a typo.
* 6fb2ba7 Render restaurants the map.
    Should say render restaurants on the map 
* 70ef834 Initial commit

## Undoing commits 
Only if we have not pushed the commit 
git reset --hard HEAD~1
    This will reset the head one space back from where it currenctly is 
    --soft Removes the commit only 
    --mixed Ustages files, Default option  
    --hard Discards local changes 
## Reverting commits 
    Pushed all of these commits to a remote repo and want to undo one or more 
git revert HEAD
    Revert just the head 
git revert HEAD~2  
    will revert just the secound
git revert HEAD~2..HEAD  
    will revert head to head~2 
A better way to revert 
git revert --no-commit HEAD~2..
    Git will figure out what the changes are and then apply them to the staging ara 
    This will revert the last two commits 
git status -s 
    See all of the changes in the staging area 
git revert --abort 
    To get out of these area 
git revert --continue 
    Happy with the changes 
    Give it a name encompasing all the reverts
Basically what that does is puts all the reverts on one line so its not as cluttered like the other method 
## Recovering Lost commits 
git reset --hard HEAD~6 
    Accidently delete 6 commits 
        Its okay, git actually hold on to them for so they can be recovered 
git reflog 
    Log of how a reference has moved in the history 
git reset --hard HEAD@{1}
    This is the last place the head was before reverting all 6 
    You can also use a the id of that entry 
        Now all th commits are back 
If we had a different branch, for example one called feature
git reflog show feature
    This will show the reference of the future pointer 
## Amending the Last Commit 
Made a commit and then realized made a mistake 
    Dont need to make a new commit, just ammend it 
echo cafe >> map.txt 
git commit -am "Render cafes on the map" 
    Commit is made 
code map.txt 
    pull up the code and make changes 
git commit --amend 
    Will pull the code back up to change the name or not 
and then your code is amended!
To add a file do the exact same thing 
git reset --mixed HEAD~1 
    This will remove the changes back to the working directory like --mixed does 
git clean -fd 
    This will remove untracked files form the working directory 
git commit -am "Render the map" 
    Now you commited just the modified text... Blue cafe

## Amending an Earlier commit 
Use interactive rebasing to amend an early commit 
git rebase -i 8441b05
    -i mean going to interact with the rebase option 
type edit in the commit you want to amend 
echo license > license.txt 
git add . 
git commit --amend 
git rebase --continue 
    You commit is amended!
        Keep in mind that its going to have to change the id for all the commits leading up to that commit
            So, only make these in a local repo that has not been shared to the remote depo yet because this is rewriting history 
## Dropping commits 
    Dropping is going to create conflicts especially if a new file is introduced. 
    This is going to be a rebase operation 
git rebase -i 72856ea^ 
 or 
git rebase -i 72856ea~1 
    Same thing. We have to rebase the parent to drop commit 
    either type drop or delete the file 
        Now resolve the conflicts
git stutus -s 
    See what is going on with the conflicts 
git log --oneline --all --graph 
    See where the changes are goiing to go 
git mergetools 
    Modify or delete the changes 
        This will apply to the next commit. 
git rebase --contiue 
    You all deleted and the changes are either deleted or modified and applyed to the next commit 
    
## Rewording commits 
    Use rebase again 
git rebase -i 6fb2ba7^ 
    replace the word pick with reword on the commits you want to reword 
It will open up the commits you want to reword 
    Reword and close the file and you are good 
Changing the name changes the commit id and all of the commits before it 
    This is rewriting history
        Do this only with the commits in the local repo 

## Reording commits 
Rebase again!
git rebase -i 70ef834
    This is the last commit so I can see all the commits 
use option-uparrow 
    To move the line you want up or down the commit list to the spot desired 

## How to squash commits together 
The parent is the commit below the one you want to work on
























 


    






 

