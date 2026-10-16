# URL
https://overthewire.org/wargames/bandit/bandit29.html

# Concepts
* Connect to a github repo and clone the repo.
  * Cloning git repo using ssh instead of http
* Find the password
  
# Method to Solve
* Brought up the man pages for git, which took me to the man pages for git clone
* Ran the clone command
  ```bash
  git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
  ```
* Access the repo and cat the README.
* Some credentials revealed but password is obfuscated
* Verifying git commit history to see if there was any previous versions with passwords leaked
  ```bash
  git log
  ```
  * reveals that the first commit fixed an info leak. Worth looking into.
  * used git revert to go back to that commit
    ```bash
    git revert --no-edit <commit-id>
    ```
  * I read the README file and password is now revealed. 
  
