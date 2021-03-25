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


