# URL
https://overthewire.org/wargames/bandit/bandit30.html

# Concepts
* Connect to a github repo and clone the repo.
  * Cloning git repo using ssh instead of http
  * Getting commit history
  * Getting branches
  * Navigating branches to find password 
* Find the password
  
# Method to Solve
* Brought up the man pages for git, which took me to the man pages for git clone
* Ran the clone command
  ```bash
  git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
  ```
* Access the repo and cat the README.
* Some credentials revealed but password is obfuscated
* Verifying git commit history to see if there was any previous versions with passwords leaked
  ```bash
  git log
  ```
  * No commits specifically mention credentials fix
  * README states no credentials in production so..... maybe dev environment?
  ```bash
  git branch -a
  ```
* Command reveals a dev branch, lets switch to it
  ```bash
  git checkout dev
  ```
* Read the README.md file.
* Got the creds!
