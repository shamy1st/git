# Git
**Git** is the most popular version control system.

### Configuration
open the configuration file /Users/<your-user>/.gitconfig

    git config --global -e

* **System** all users
* **Global** all repositories of the current user
  * **Name**
  
        git config --global user.name "Ahmed Elshamy"
        
  * **Email**
  
        git config --global user.email ahmed.elshamy@example.com
        
  * **Default Editor**
  
        git config --global core.editor "code --wait"
        
  * **Line Ending**
* **Local** the current repository
