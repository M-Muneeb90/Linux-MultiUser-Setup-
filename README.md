# Linux Multi-User Collaboration Setup (System Admin Lab)

This project demonstrates how to create a multi-user collaboration environment in Linux with specific group permissions.

## Steps Performed & Commands Used:

### Step 1: User Creation & Password Setup
Created two users named `user1` and `user2` and immediately assigned passwords to them so they can log in.
* **Commands to add users:**
  ```bash
  sudo useradd user1
  sudo useradd user2
  ```
* **Commands to set passwords:**
  ```bash
  sudo passwd user1
  sudo passwd user2
  ```

### Step 2: Group Creation
Created a new group named `developers` to manage our collaborative users.
* **Command to create group:**
  ```bash
  sudo groupadd developers
  ```

### Step 3: Adding Users to Group
Added both `user1` and `user2` into the newly created `developers` group.
* **Command used:**
  ```bash
  sudo gpasswd -a user1 developers
  sudo gpasswd -a user2 developers
  ```

### Step 4: Creating the Shared Folder
Created a shared folder named `projects` inside the administrator's home directory.
* **Command used:**
  ```bash
  mkdir projects
  ```

### Step 5: Changing Ownership
Changed the owner of the folder to `root` and the group ownership to `developers`.
* **Commands used:**
  ```bash
  sudo chown root projects
  sudo chgrp developers projects
  ```

### Step 6: Setting Permissions
Configured the folder permissions using `chmod` so that only members of the `developers` group can create, read, or edit files inside it.
* **Command used:**
  ```bash
  sudo chmod 770 projects
  ```

### Step 7: Testing & Collaboration Verification
Verified the setup by switching users, accessing the absolute path, writing text using `vi` editor, and modifying it with the second user.

* **Testing with user1 (Creating and writing text):**
  ```bash
  su - user1
  cd /home/administrator/projects
  vi lab_test.txt
  
  # Inside vi Editor:
  # 1. Pressed 'i' to enter Insert Mode and typed the text.
  # 2. Pressed 'ESC' key to exit Insert Mode.
  # 3. Typed ':wq' and pressed Enter to Save and Exit.
  
  exit
  ```

* **Testing with user2 (Verifying and editing changes):**
  ```bash
  su - user2
  cd /home/administrator/projects
  vi lab_test.txt
  
  # Inside vi Editor:
  # 1. Pressed 'i' to add new changes.
  # 2. Pressed 'ESC' key to exit Insert Mode.
  # 3. Typed ':wq' and pressed Enter to Save and Exit.
  
  exit
  ```
