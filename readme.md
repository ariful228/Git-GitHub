# GIT
! Git is a distributed version control system that allows developers to track project changes and collaborate efficiently.
* ***Track history:*** Every change is saved, can review or revert to any point.
* ***Collaboration:*** Multiple people can work on the same project, each contributing their changes.<br><br> 
>[!NOTE] Git is known for being fast, open-source, stable, and widely popular among developers.* <br><br> <br> 

<br><br><br>

# GitHub
>[!NOTE]
 GitHub is a cloud-based platform for hosting Git repositories, allowing for easy collaboration and project management.<br> 
   ***Store and manage code:*** GitHub provides a remote repository where code is securely stored.<br> 
   ***Collaborate:*** Invite others to contribute, review, or comment on the code.   <br>

<br><br><br>

# Install, Config, and Account:
## Install Git:
>[!IMPORTANT]
[Download and install Git from the official site:](https://git-scm.com) <br>
Verify the installation:<br>
`git --version`

<div style="border: 1px solid #000000; padding: 10px; border-radius: 5px; background-color: ##000000; color: ##d4edda;">
  <strong>CONFIGURATION</strong>  
  <p>Configure Git: (This will be linked to your GitHub/GitLab account)</p>

  <strong>User information:</strong>  
  <pre>
  git config --global user.name "Your Name"
  git config --global user.email "your.email@example.com"
  git config --list  # Verify the configuration
  </pre>
</div>

<br><br><br>


## Create a GitHub (or GitLab) Account:
>[!NOTE]
  - Go to GitHub or GitLab and create an account.
  - After creating the account, need to link local Git repository to a remote repository on these platforms.

# Clone a Repository
>[!TIP]
 -Cloning a repository copies the remote repository to  local machine.<br>
 -Clone a remote repository:<br>
 `git clone <repository_link>`<br>
 -Check the status of  local repository:<br>
 `git status`

## File States in Git
### Git tracks files in different states:
>[!WARNING]
    ***Untracked:*** New files that haven’t been added yet. <br>
    ***Modified:*** Files that have been changed but not staged for commit.<br>
    ***Staged:*** Files prepared for the next commit.<br>
    ***Unmodified:*** Files that are unchanged since the last commit.<br>

<details style="border: 1px solid #000000; padding: 10px; border-radius: 5px; background-color: #f9f9f9; color: #000000;">
    <summary> Basic Git Workflow </summary> 
    
    Add changes to staging:
    git add <file_name>

    Commit changes with a message: 
    git commit -m " commit message"

    Push changes to the remote repository:
    git push origin main

    Set upstream for future pushes (only needed once):
    git push -u origin main

   
</details>


<br><br><br> 

# Git init:
> [!IMPORTANT]
> ***Start Version Control for a New Project:***  
> - Initialize Git in a project directory using `git init`.  
> - This sets up Git tracking in the project folder, allowing to manage versions and track changes.  
>  
> ***Initialize a Repository Without a Remote:***  
> - When starting a brand-new project that doesn’t yet exist in any remote repository (like on GitHub or GitLab), `git init` is essential for keeping track of changes locally.  
> - Add a remote later using `git remote add origin` once a remote repository has been created.  
>  
> ***Complete Local-Only Work:***  
> - `git init` serves as the starting point for tracking changes without needing to clone an existing repository.

<details style="border: 1px solid #000000; padding: 10px; border-radius: 5px; background-color: #f9f9f9; color: #000000;">
   <summary> Initial Git Workflow </summary>
   
    For new projects, initialize Git and link to a remote repository:
    Initialize a new Git repository:
    git init

    Add the remote repository link:
    git remote add origin <repository_link>

    Verify the remote link:<br>
    git remote -v

    Set the branch to main and push the code:
    git branch -M main
    git push -u origin main
</details>
<br><br>

# Branching
Branches in Git allow to work on different features, bug fixes, or experimental code independently from the main project without affected main codebase until to merge.

>[!NOTE]
>  
> ***Why Branching is Important:***  
> - **Parallel development:** Allows multiple developers to work on different features or fixes simultaneously.  
> - **Isolated testing:** Each branch can be tested independently without affecting the main project.  
> - **Version control:** Different versions of the codebase can be maintained and merged back into the main branch when ready.   


<details style="border: 1px solid #000000; padding: 10px; border-radius: 5px; background-color: #f9f9f9; color: #000000;">
    <summary>Branching command: </summary>

        Create a new branch:
        git checkout -b <branch_name>
        Example: 
        git checkout -b feature1
        ..............................

        Switch to an existing branch: 
        git checkout <branch_name>
        Example: 
        git checkout main
        ..............................

        List all branches: 
        git branch
        ..............................

        Delete a branch: 
        git branch -d <branch_name>
        Example: 
        git branch -d feature1

        Force delete a branch: 
        git branch -D <branch_name>
    ...............................
</details>

<br><br>

# Merging
Merging is the process of integrating changes from one branch into another.

## How Merging Works:
Git looks at the changes made in both branches and combines them. If there are conflicting changes (e.g., modifications to the same lines in the same file), Git will pause and ask  to resolve the conflict manually.

<details style="border: 1px solid #000000; padding: 10px; border-radius: 5px; background-color: #f9f9f9; color: #000000;">
    <summary> Steps to Merge a Branch: </summary>

    Switch to the target branch (usually main): 
    git checkout main

    Merge another branch into the current branch: 
    git merge <branch_name>

    Example: 
    git merge feature1

    Resolve merge conflicts (if any): 
    git add <file_with_conflicts>
    git commit -m "Resolved merge conflicts"

</details>

### Using Pull Requests (PRs) for Merging (GitHub)
For teams or collaborative projects, it's common to use Pull Requests (PRs) on platforms like GitHub to review code before merging.
<details style="border: 1px solid #000000; padding: 10px; border-radius: 5px; background-color: #f9f9f9; color: #000000;">
    <summary>Pull Request Workflow: </summary>
    Create a branch for  changes locally (e.g., feature1):
    git checkout -b feature1

    Push  branch to the remote repository:
    git push origin feature1

    Open a Pull Request (PR):
    1- Go to GitHub and navigate to  repository.
    2- Click on the "Pull Requests" tab and create a new PR for  branch.
    3- The PR allows others to review  code before merging it into the main branch.

    Merge the PR once approved: 
    After the code is reviewed and approved, merge the PR through the GitHub interface. This integrates  changes into the target branch (typically main).
</details>

<br><br>

# Resolve Merge Conflicts
Conflicts occur when changes in two branches overlap and Git cannot decide how to combine them.
example:
```
Scenario:
Branch01: Modified index.html at line 2 to <p> up </p>.
Branch02: Modified index.html at line 2 to <p> down </p>.
The goal is to keep both changes in one branch.
```

<details style="border: 1px solid #000000; padding: 10px; border-radius: 5px; background-color: #f9f9f9; color: #000000;">
    <summary>Merge Conflict:</summary>

    Create and switch to a new branch (if not already on one of the branches):
    `git checkout branch01`

    Merge branch02 into branch01:
    `git merge branch02`

    ***This will trigger a merge conflict because both branches changed the same line in index.html.


    Git will now pause the merge and mark the conflict in *index.html*.  will see something like this in the file:
    <<<<<<< HEAD (current change)
    <p> up </p>
    =======
    <p> down </p>
    >>>>>>> branch02(Incoming change)

</details>
<br>
<details style="border: 1px solid #000000; padding: 10px; border-radius: 5px; background-color: #f9f9f9; color: #000000;">
    <summary>Manually resolve the conflict by editing the file</summary> 
    In this case, we want to keep both lines in *index.html*:
    <p> up </p>
    <p> down </p>

    Stage the resolved file:
    git add index.html

    Complete the merge by committing the changes:
    git commit -m "Resolved merge conflict in index.html by keeping both lines"

    Push the changes to the remote repository:
    git push origin branch01
  
    Now, the conflict is resolved, and both changes from branch01 and branch02 are merged into branch01.
</details>

<br><br>

# Undo Changes
Git allows undoing changes at different stages:

<details style="border: 1px solid #000000; padding: 10px; border-radius: 5px; background-color: #f9f9f9; color: #000000;">
    <summary>Unstage changes</summary> 

    Remove a file from the staging area but keep changes:
    git reset <file_name>

    Undo the last commit but keep changes
    git reset HEAD~1

    Reset to a previous commit (removes all changes after it)
    git reset --hard <commit_hash>

</details>
<br>

<details style="border: 1px solid #000000; padding: 10px; border-radius: 5px; background-color: #f9f9f9; color: #000000;">
  <summary>Example</summary>
  
  ### Reverting Commits:
  - Commit 1 > Commit 2 > Commit 3 > Commit 4

  - **Undo the last commit** (move from 4 to 3):
    ```bash
    git reset HEAD~1
    ```

  - **Reset to a specific commit** (move from 4 to 2, remove changes):
    ```bash
    git reset --hard <commit_hash_of_commit_2>
    ```

  - **Reset to a specific commit** (move from 4 to 2, keep changes):
    ```bash
    git reset <commit_hash_of_commit_2>
    ```
  
</details>


<br><br>

# Git Log
>[!IMPORTANT]
 Git log is a tool that allows to view the commit history of repository. It provides detailed information about each commit, such as commit hash, author, date, and commit message.

## View commit history:
To see the full commit history of the repository, use:<br>
`git log`

>[!NOTE]
***This will show a list of all commits like:***<br>
    Commit hash<br>
    Author<br>
    Date and time of the commit<br>
    Commit message<br>
  

<details style="border: 1px solid #000000; padding: 10px; border-radius: 5px; background-color: #f9f9f9; color: #000000;">
    <summary style="font-weight: bold; font-size: 1.1em;">🔍 Git Log Commands</summary>
    View a simplified, one-line log:
    git log --oneline
    
    Limit the number of commits displayed:
    git log -n <number_of_commits>

    For example, to view only the last 3 commits:
    git log -n 3
    
    View commits by a specific author:
    git log --author="Author Name"
    
    View changes in each commit:<br>
    git log -p
</details>


<br><br>

# Fork (GitHub)
>[!NOTE]
 A fork is a copy of a repository that lives under GitHub account. Forking allows to make changes to a project to contribute without affecting the original repository.


## Steps to fork a repository:
*Fork the repository:* <br>
>1- On the GitHub repository page, click the "Fork" button. <br>
>2- This creates a copy of the repository under  GitHub account.

***Clone the forked repository to  local machine:*** <br>

<details style="border: 1px solid #000000; padding: 10px; border-radius: 5px; background-color: #f9f9f9; color: #000000;">
    <summary style="font-weight: bold; font-size: 1.1em;">🔄 Clone Forked Repository</summary>
    
    After forking, clone the repository locally:
    git clone <forked_repository_link>

    Make changes and push them to  fork: 
    git add <files>
    git commit -m "Description of  changes"
    git push origin <branch_name>
</details>

<br>

***Submit a Pull Request:***<br>

* To contribute changes back to the original repository, create a Pull Request (PR) from fork to the original repository. 
* This allows the project maintainers to review  changes and merge them if appropriate.

*Forking is commonly used in open-source collaboration, allowing developers to freely experiment without affecting the original codebase.*
