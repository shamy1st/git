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

* **Skipping the staging area**

        git commit -am "Message"

* **List files in staging area**

        git ls-files

* **Removing files**

        git rm file1.js                 # Removes from working directory and staging area
        git rm --cached file1.js        # Removes from staging area only

* **Renaming or moving files**

        git mv file1.js file1.txt

* **all gitignore file templates for all languages**
    https://github.com/github/gitignore

* **gitignore file template for java**
    https://github.com/github/gitignore/blob/master/Java.gitignore


