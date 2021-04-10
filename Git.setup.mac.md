## How to set up git on mac 
download homebrew 
download git 
download oh my zsh 
    
## change theme 
    go to finder 
        cmd-shift-. to show hidden files
            cmd-shft-h to go to user 
                open .zshrc 
                    Change the theme to whatever

## Open a local repo 
create the folder or directory 
git init
    This creates a local repo 
git remote add origin url 
    To add a remote repo 
        Now you are connected and good to go!
    touch .gitiginore 
        Create a .gitignore file and put DS store if it comes up 
            add .DS_Store before first commit it
            or 
            if already commited then git rm --cached .DS.Store

cloneing a repo: 
git clone url 
git remote add origin url 
git pull origin url 
    Now you have all the content 

