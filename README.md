# Git
**Git** is the most popular version control system.

### Configuration
open the configuration file /Users/your-user/.gitconfig

    git config --global -e

* **System** all users
* **Local** the current repository
* **Global** all repositories of the current user
  * **Name**
  
        git config --global user.name "Ahmed Elshamy"
        
  * **Email**
  
        git config --global user.email ahmed.elshamy@example.com
        
  * **Default Editor**
  
        For "Visual Studio Code"
        git config --global core.editor "code --wait"
        
  * **Line Ending**
  
        For MacOs / Linux
        git config --global core.autocrlf input
        
        For Windows
        git config --global core.autocrlf true
  
    ![](https://github.com/shamy1st/git/blob/main/config-line-ending-1.png)
    ![](https://github.com/shamy1st/git/blob/main/config-line-ending-2.png)

### Snapshots

* **Initializing a repository**
        
        git init

* **Staging files**

        git add file1.js                # Stages a single file
        git add file1.js file2.js       # Stages multiple files
        git add *.js                    # Stages with a pattern
        git add .                       # Stages the current directory and all its content                                       

* **Viewing the status**

        git status                      # Full status
        git status -s                   # Short status

* **Committing the staged files**

        git commit -m "Message"         # Commits with a one-line message
        git commit                      # Opens the default editor to type a long message
        git commit -am "Message"        # Skipping the staging area

* **List files in staging area**

        git ls-files

* **Removing files**

        git rm file1.js                 # Removes from working directory and staging area
        git rm --cached file1.js        # Removes from staging area only

* **Renaming or moving files**

        git mv file1.js file1.txt

* **gitignore**
    * [All Programming languages templates](https://github.com/github/gitignore)
    * [Java template](https://github.com/github/gitignore/blob/master/Java.gitignore)

* **Viewing the staged/unstaged changes**

        git diff                        # Shows unstaged changes (working directory vs staging area)
        git diff --staged               # Shows staged changes (staging area vs committed)
        git diff --cached               # Shows staged changes (staging area vs committed)

* **Visual Diff Tools**

        # set default diff tool to "Visual Studio Code"
        git config --global diff.tool vscode                                            
        # tell git how to run diff tool, check .gitconfig file because "$LOCAL $REMOTE" is missing
        git config --global difftool.vscode.cmd "code --wait --diff $LOCAL $REMOTE"
        
        git difftool                    # Shows unstaged changes (working directory vs staging area)
        git difftool --staged           # Shows staged changes (staging area vs committed)
        
* **Viewing the history**

        git log                         # Full history (newest to oldest)
        git log --reverse               # Full history (oldest to newest)
        git log --oneline               # Summary (newest to oldest)
        git log --oneline --reverse     # Summary (oldest to newest)
        
* **Viewing a commit**

        git show 921a2ff                # Shows the given commit
        git show HEAD                   # Shows the last commit
        git show HEAD~2                 # Two steps before the last commit
        git show HEAD:file.js           # Shows the version of file.js stored in the last commit
        
* **Unstaging files (undoing git add)**

        git restore --staged file.js    # Copies the last version of file.js from repo to index
        
* **Discarding local changes**

        git restore file.js             # Copies file.js from index to working directory
        git restore file1.js file2.js   # Restores multiple files in working directory
        git restore .                   # Discards all local changes (except untracked files)
        git clean -fd                   # Removes all untracked files
        
* **Restoring an earlier version of a file**

        git restore --source=HEAD~1 file.js

### Browsing History

* **Viewing the history**

        git log --stat                  # Shows the list of modified files
        git log --patch                 # Shows the actual changes (patches)
        
* **Filtering the history**

        git log -3                      # Shows the last 3 commits
        git log --author="Ahmed"
        git log --before="2020-10-30"
        git log --after="one week ago"
        git log --grep="GUI"            # Commits with “GUI” in their message (case-sensitive)
        git log -S"GUI"                 # Commits with “GUI” in their content (case-sensitive)
        git log hash1..hash2            # Range of commits
        git log file.txt                # Commits that touched file.txt
        
* **Formatting the log output** [docs](https://git-scm.com/docs/git-log)

        git log --pretty=format:"%Cgreen%an%Creset committed %h %cd"

* **Creating an alias**

        git config --global alias.lg "log --pretty=format:'%Cgreen%an%Creset committed %h %cd'"

* **Viewing a commit**

        git show HEAD~2
        git show HEAD~2:file1.txt       # Shows the version of file stored in this commit
        git show HEAD~2 --name-only     # Shows files names only without modifications detail
        git show HEAD~2 --name-status   # Shows files names with indicator modified or not with details

* **Comparing commits**

        git diff HEAD~2 HEAD            # Shows the changes between two commits
        git diff HEAD~2 HEAD file.txt   # Changes to file.txt only
        

* **Checking out a commit**

        git checkout dad47ed            # Checks out the given commit
        git checkout master             # Checks out the master branch
        
* **Finding a bad commit**

        git bisect start                # start a new bisect branch
        git bisect bad                  # Marks the current commit as a bad commit
        git bisect good ca49180         # Marks the given commit as a good commit
        git bisect reset                # Terminates the bisect session
        
* **Finding contributors**

        git shortlog
          
* **Viewing the history of a file**

        git log file.txt                # Shows the commits that touched file.txt
        git log --stat file.txt         # Shows statistics (the number of changes) for file.txt
        git log --patch file.txt        # Shows the patches (changes) applied to file.txt
        
* **Finding the author of lines**

        git blame file.txt              # Shows the author of each line in file.txt
        git blame -L 5,10 file.txt      # Shows the author of lines 5 to 10
        
* **Tagging**

        git tag v1.0                    # Tags the last commit as v1.0
        git tag v1.0 5e7a828            # Tags an earlier commit
        git tag                         # Lists all the tags
        git tag -d v1.0                 # Deletes the given tag

### Branching & Merging

* **Managing branches**

        git branch bugfix                           # Creates a new branch called bugfix
        git branch -m bugfix bugfix/signup-form     # Rename branch
        git checkout bugfix                         # Switches to the bugfix branch
        git switch bugfix                           # Same as the above
        git switch -C bugfix                        # Creates and switches
        git branch -d bugfix                        # Deletes the bugfix branch
        
* **Comparing branches**

        git log master..bugfix              # Lists the commits in the bugfix branch not in master
        git diff master..bugfix             # Shows the summary of changes
        git diff bugfix                     # If current branch is master, it will list the differences
        git diff --name-status bugfix       # List only difference files with status
        
* **Stashing**

        git stash push -m "New tax rules"   # Creates a new stash
        git stash list                      # Lists all the stashes
        git stash show stash@{1}            # Shows the given stash
        git stash show 1                    # shortcut for stash@{1}
        git stash apply 1                   # Applies the given stash to the working dir
        git stash drop 1                    # Deletes the given stash
        git stash clear                     # Deletes all the stashes
        
* **Merging**

        git log --oneline --all --graph     # 
        git merge bugfix                    # Merges the bugfix branch into the current branch (fast-forward by default)
        git merge --abort                   # Aborts the merge (if you find a conflicts and no time to solve)
        
    * **Fast-Forward Merge**: if the branches have not diverged.
        * only move pointer to the last commit in the branch
        * to prevent fast-forward merge use "--no-ff" with "merge" command
                
                git config ff no                # Disable any fast-forward merge in current repository.
                git config --global ff no       # Disable any fast-forward merge in all repositories.
        
        ![](https://github.com/shamy1st/git/blob/main/fast-forward-merge.png)
        
    * **3-Way Merge**: if the branches diverged.

            git merge --no-ff bugfix            # Creates a merge commit even if FF is possible
            
        ![](https://github.com/shamy1st/git/blob/main/3way-merge.png)

    * **Squash Merge**: 
    
            git merge --squash bugfix           
            git commit -am "Message"
            git branch -D bugfix
        
        ![](https://github.com/shamy1st/git/blob/main/squash-merge-1.png)
        ![](https://github.com/shamy1st/git/blob/main/squash-merge-2.png)
        ![](https://github.com/shamy1st/git/blob/main/squash-merge-3.png)

* **Viewing the merged branches**

        git branch --merged             # Shows the merged branches
        git branch --no-merged          # Shows the unmerged branches

* **Merge Conflicts**
1. change into single file by two different ways.
2. delete a file in a branch, and update it in another.
3. add new file but the content is different.

* **Merge Tools**

        git mergetool                   # Launch the default merge tool.

    * p4merge
            
            #set default merge tool
            git config --global merge.tool p4merge
            git config --global mergetool.p4merge.path "/Applications/p4merge.app/Contents/MacOS/p4merge"
            
            #prevent mergetool to keep backup files
            git config --global mergetool.keepBackup false
            
    * kdiff
    * winmerge (windows only)

* **Undoing a Faulty Merge**
    * **revert**
            
            git revert -m 1 HEAD
            
    * **resetting**
        * **soft**
        ![](https://github.com/shamy1st/git/blob/main/reset-soft.png)
        * **mixed**
        ![](https://github.com/shamy1st/git/blob/main/reset-mixed.png)
        * **hard**

                git reset --hard HEAD~1
            ![](https://github.com/shamy1st/git/blob/main/reset-hard.png)

* **Rebasing**

        git rebase master               # Changes the base of the feature branch (do it in the feature branch)
        git switch master               # Switch to master branch
        git merge feature               # Fast-forward merge
        
        git rebase --continue           # If conflict happen solve it then continue rebase
        git rebase --abort              # Cancel rebase
        git rebase --skip               # Skip current commit of rebase if it is not important!

    ![](https://github.com/shamy1st/git/blob/main/rebase-1.png)
    ![](https://github.com/shamy1st/git/blob/main/rebase-2.png)
    ![](https://github.com/shamy1st/git/blob/main/rebase-3.png)

* **Cherry picking**

        git cherry-pick dad47ed         # Applies the given commit on the current branch
        
    ![](https://github.com/shamy1st/git/blob/main/cherry-pick-1.png)
    ![](https://github.com/shamy1st/git/blob/main/cherry-pick-2.png)
    ![](https://github.com/shamy1st/git/blob/main/cherry-pick-3.png)
        
### Collaboration

* **Cloning a repository**

        git clone url
        
* **Syncing with remotes**

        git fetch origin master         # Fetches master from origin
        git fetch origin                # Fetches all objects from origin
        git fetch                       # Shortcut for "git fetch origin"
        git pull                        # Fetch + merge
        git push origin master          # Pushes master to origin
        git push                        # Shortcut for "git push origin master"
        
* **Sharing tags**

        git push origin v1.0            # Pushes tag v1.0 to origin
        git push origin —delete v1.0    
        
* **Sharing branches**

        git branch -r                   # Shows remote tracking branches
        git branch -vv                  # Shows local & remote tracking branches
        git push -u origin bugfix       # Pushes bugfix to origin
        git push -d origin bugfix       # Removes bugfix from origin
        
* **Managing remotes**

        git remote                      # Shows remote repos
        git remote add upstream url     # Adds a new remote called upstream
        git remote rm upstream          # Remotes upstream

### Rewriting History

* **Undoing commits**
        git reset --soft HEAD^          # Removes the last commit, keeps changed staged
        git reset --mixed HEAD^         # Unstages the changes as well
        git reset --hard HEAD^          # Discards local changes
        
* **Reverting commits**

        git revert 72856ea                  # Reverts the given commit
        git revert HEAD~3..                 # Reverts the last three commits
        git revert --no-commit HEAD~3..     
        
* **Recovering lost commits**

        git reflog                      # Shows the history of HEAD
        git reflog show bugfix          # Shows the history of bugfix pointer
        
* **Amending the last commit**

        git commit --amend
        
* **Interactive rebasing**

        git rebase -i HEAD~5

