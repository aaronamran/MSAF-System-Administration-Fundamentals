# Run A Bash Script As Another User Without Their Password
Linux has multiple methods of executing scripts or commands as another user. Usually this requires the input of the other user's password. Fortunately, there are methods in which a user can execute a command as another user without knowing their password


## Tasks
- In a Linux VM, create two user accounts
- Create a simple 'Hello World' bash script
- Use chmod to make the script executable by user2
- Confirm that user1 cannot execute the script
- Modify the sudoers file to allow user1 to perform actions as user2 without their password


## Benchmarks
- Run 'whoami' to confirm that the current session is running under the user1 context
- As user1, execute the script


## Practical Approach
1. In Lubuntu VM, create 2 user accounts; user1 and user2:
   ```
   sudo adduser user1
   sudo adduser user2
   ```
   Set passwords for each user during the creation process as prompted
2. Login as user2
   ```
   su - user2
   ```
3. Create a simple Bash script in their home directory:
   ```
   nano ~/hello.sh
   ```
4. Add the following content to the script
   ```
   #!/bin/bash
   echo "Hello, World!"
   ```
5. Save the file and make it executable
   ```
   chmod +x ~/hello.sh
   ```
   Then logout from user2 back to user1
   ```
   exit
   ```
6. Login as user1 and try to execute the script
   ```
   /home/user2/hello.sh
   ```
   A "Permission denied" error should be displayed because user1 does not have the required permissions
7. Log back in as user2 and update the script permissions
   ```
   chmod o+x ~/hello.sh
   ```
8. Confirm the script is executable by others
   ```
   ls -l ~/hello.sh
   ```
9. Exit and login as admin and use the following to adjust permissions for user2's home directory
   ```
   sudo chmod o+x /home/user2
   ```
10. Switch back to user1 and try executing the script again
   ```
   /home/user2/hello.sh
   ```
   This time, the script should execute successfully
11. To modify the sudoers file to allow password-less execution, open the sudoers file for editing
    ```
    sudo visudo
    ```
12. Then add the following line to allow user1 to execute commands as user2 without a password
    ```
    user1 ALL=(user2) NOPASSWD: /home/user2/hello.sh
    ```
    Save and close the file
13. Login as user1 and verify the current user context
    ```
    whoami
    ```
14. Run the script as user2 using sudo
    ```
    sudo -u user2 /home/user2/hello.sh
    ```
    Confirm the script executes successfully





