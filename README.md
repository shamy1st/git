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

### Branching

* ****

        
        
* ****

        
        
