# Pre-Installation Kit for SAS 9.4 Systems (PIK for 9.4)

This Ansible playbook performs the tasks required to install a typical SAS 9.4 deployment on Red Hat Enterprise Linux 7 and 8.


## Prerequisites for Running the Pre-installation Playbook
Before running this playbook, perform the following steps:
* Install a suitable version of Ansible. (2.9 or 2.8)
* Verify that the user has sudoers privileges.

* Create a secret file containing encrypted values for a variable password by using ansible-vault create vars/password.yaml. Set the password to your password and enter the following line: (You can skip this step by skipping useroperations)
  ```
  pw: your-password
  ```

## Running the Playbook
To run the whole playbook, execute the following command:
  ```
  ansible-playbook --ask-vault-pass pik.yaml
  ```
  It will ask you the password that you have chosen while creating password.yaml file

If you want to skip certain parts of the playbook or run ony a certain part of playbook you need to give ```--tags``` or ```--skip-tags``` flags.
  ```
  ansible-playbook --skip-tags=useroperations pik.yaml
  ```

## Useful Optional Arguments
* ```--check``` or ```-C```: Executes a "dry run" of the playbook, running the playbook without making changes to the system. 
* ```-v through -vvvv```: Lets you increase the verbosity of the script output.

## What does this Playbook do?
* Checks the system for 
  * Operating System
  * Memory
  * CPU Cores
* Creates groups and users. Assigns password for users.
* Create directories and sets its user, group, permission settings
* Installs required packages
* Sets the PAM limits
  

## Flags
* packageoperations: Updates all packages and installs required third-party packages
* update: Handles update of all packaes
* useroperations: Creates groups, users and sets password for users 
* directories: Creates folders and sets its permissions 
* limitoperations: Handles PAM limits
