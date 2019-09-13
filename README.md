## Git in Action

This repository is used for practice on Git, 
include basic commands and basic knowledge.

#### Basic Concept
1. What is Git?  
[---- image here ----]  
> Git is a free and open source **distributed version control system** 
> designed to handle everything from small to very large projects
> with **speed and efficiency**.  

- What is version control system (VCS/SCM)?
> the management of changes to documents, computer programs, large websites,
> and other collection of information

- Why distributed?  
Compared with traditional centralize version control system(CVCS) like Subversion(SVN),
it avoids the single point failure, which means if the server down or lose data, no one 
can connect to the server to retrieve the code and even lose the change history.

- Why speed and efficiency?  
Git records the snapshots instead of differences   
other tools :  record the difference between each version, 
it takes time to switch to another version or branch  
[---- image here ----]  
Git : records the snapshots, use SHA-1 hash, 40-character string, 
can use shorter string as long as it's unique  
[---- image here ----]  

2. Working directory / staging area / local repository / remote repository  
[---- image here ----]  

3. origin / master / HEAD  
- origin : default name of remote repository  
    ``git remote add orgin git@github.com:allenwhm/git-in-action.git``  
- master : default name of first branch  
- HEAD : name of current branch, it's a pointer  
[---- image here ----]  

#### Basic Action  
1. config username / email
- config scope  
    current repository : .git/config  
    global, for all repositories in current user --global : ~/.gitconfig
    system, for all uses in current system --system : /etc/gitconfig  
- list config  
    ``git config --list [--global/system]``  
- config username / email  
    ```
    git config --global user.name "allen"   
    git confif --global user.email "allen@wang.com"
    ```
- command alias  
    ```
    git config --global alias.co checkout
    git config --global alias.br branch
    git config --global alias.ci commit
    git config --global alias.st status
    git config --global alias.unstage 'reset HEAD --'
    git config --global alias.last 'log -1 HDEA'
    ```
- cancel alias
    ``git config --global --unset alias.st``
    
2. clone a repo from remote server  
- clone : git clone repo_url [new_repo_name]
    ``git clone git@github.com:allenwhm/git-in-action.git``
- git protocol
    - local protocol : based on file systems
    - git : no authentication, fastest
    - SSH : need add SSH ket into authorized_keys
    - HTTP/HTTPS : most convenient, with authentication 
    
3. init a repo with current project and publish it to git server(GitHub/Bitbucket)
- init repo : change directory to project folder  
    ```
    cd project_directory
    git init
    ```
- create .gitignore file to ignore files not required to be tracked
    ``echo target > .gitignore``    
- add files into staging area (working directory -> staging area)  
add all files  
    ``git add --all / * / .``  
add one file  
    ``git add file_name``
- commit changes to local repo (staging area -> local repo)  
commit and write message in editor
    ``git commit``  
commit and write message at the same time  
    ``git commit -m "commit message" ``  
add and commit in one step  
    ```
    git commit -am "add and commit in one step"
    git commit -a -m "add and commit in one step"
    ```  
  commit --amend : commit again, and replace the last commit
    ```
    git commit -am "some commit here"
    some changes
    git commit --amend "latest commit"
    ```
- add remote repo fpr current repo
    
