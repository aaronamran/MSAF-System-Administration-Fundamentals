# Use JohnTheRipper To Find Weak User Passwords In Linux
John the Ripper is a password security auditing and password recovery tool. It autodetects the encryption on the hashed data and compares it against a large text file. The file contains popular passwords. It hashes each password, and stops when it finds a match

## References
- [John the Ripper password cracker](https://www.openwall.com/john/) by Openwall
- [How to check for weak passwords on your Linux systems with John the Ripper](https://www.techrepublic.com/videos/how-to-check-for-weak-passwords-on-your-linux-systems-with-john-the-ripper/) by Jack Wallen on TechRepublic


## Tasks
- Download and install JohnTheRipper (JtR) on a Linux VM. You may also use Kali which comes pre-configured with JohnTheRipper
- Create a new sudo user on the machine with weak password (for example, password123)
- Run JohnTheRipper against user passwords
- Demonstrate that you can identify the password of the new user using JohnTheRipper


## Practical Approach
1. To verify that John The Ripper (JtR) is installed in a Linux VM, use
   ```
   john --help
   ```
   Otherwise, run the commands
   ```
   sudo apt update && sudo apt install john -y
   ```
2. To create a new sudo user with a weak passwords, use
   ```
   sudo adduser weakuser
   ```
   Add a weak password like `password123`
3. To grant sudo privileges to the new user, use
   ```
   sudo usermod -aG sudo weakuser
   ```
4. Verify that the new user now has sudo privileges using
   ```
   sudo -l -U weakuser
   ```
5. To crack passwords with JtR, password hashes stored in `/etc/shadow` are needed. Since this file is restricted to the root user, copy `/etc/shadow` and `/etc/passwd` for testing
   ```
   sudo cp /etc/shadow /tmp/shadow
   sudo cp /etc/passwd /tmp/passwd
   ```
6. Ensure that permissions and access are allowed for testing
   ```
   sudo chmod 644 /tmp/shadow /tmp/passwd
   ```
7. Combine files into a single format JtR can use. Use the `unshadow` utility
   ```
   sudo unshadow /tmp/passwd /tmp/shadow > /tmp/unshadowed.txt
   ```
8. Run JtR on the unshadowed file by using the default wordlist
   ```
   john /tmp/unshadowed.txt
   ```
   Check the progress or results
   ```
   john --show /tmp/unshadowed.txt
   ```
