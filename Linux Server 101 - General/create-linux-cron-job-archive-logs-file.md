# Create A Cron Job On A Linux Server To Archive Logs File Every 24 Hours
The Cron daemon is a built-in Linux utility that runs processes on your system at a scheduled time. Cron reads the crontab (Cron tables) for predefined commands and scripts. You can configure a Cron job to schedule scripts or other commands to run automatically


## References
- [How I use cron in Linux](https://opensource.com/article/17/11/how-use-cron-linux=) by David Both on opensource.com


## Tasks
- Setup a Linux VM in VirtualBox
- Install and configure ClamAV
- Create a cron job that runs a deep malware scan every 12 hours using ClamAV
- Create a cron job that monitors RAM, CPU and Disk utilization every 3 hours
- Create a cron job that reboots the machine at 3 AM every Monday
- Save all results to a log file



## Benchmarks
- Show all results are being stored in the respecting log files


## Practical Approach
1. For this task, Lubuntu VM in VirtualBox is used. ClamAV needs to be installed too
   ```
   sudo apt install cron vim clamav clamav-daemon -y
   ```
2. Verify that Cron is running
   ```
   sudo systemctl enable cron
   sudo systemctl start cron
   ```
3. Update ClamAV virus definitions using
   ```
   sudo freshclam
   ```
4. Perform a test scan to verify functionality
   ```
   sudo clamscan --infected --remove --recursive /home
   ```
5. To create cron jobs for deep malware scan every 12 hours, create a shell script and save it to `/usr/local/bin/deep-malware-scan.sh`
   ```
   sudo vim /usr/local/bin/deep-malware-scan.sh
   ```
   In the script, add the following code
   ```
   #!/bin/bash
   LOG_FILE="/var/log/deep-malware-scan.log"
   clamscan -r / --log=$LOG_FILE
   ```
   Make the script executable
   ```
   sudo chmod +x /usr/local/bin/deep-malware-scan.sh
   ```
   To add a cron job, open the crontab file
   ```
   crontab -e
   ```
   Add the following line to schedule the malware scan every 12 hours
   ```
   0 */12 * * * /usr/local/bin/deep-malware-scan.sh
   ```
6. To create a cron job for monitoring RAM, CPU and disk utilisation every 3 hours create a shell script and save to `/usr/local/bin/system-monitor.sh`
   ```
   sudo vim /usr/local/bin/system-monitor.sh
   ```
   In the shell script, add the following code
   ```
   #!/bin/bash
   LOG_FILE="/var/log/system-monitor.log"
   echo "RAM Usage:" >> $LOG_FILE
   free -h >> $LOG_FILE
   echo "CPU Usage:" >> $LOG_FILE
   top -bn1 | grep "Cpu(s)" >> $LOG_FILE
   echo "Disk Usage:" >> $LOG_FILE
   df -h >> $LOG_FILE
   echo "----------------------------------" >> $LOG_FILE
   ```
   Make the script executable using
   ```
   sudo chmod +x /usr/local/bin/system-monitor.sh
   ```
   To add a cron job, open the crontab file
   ```
   crontab -e
   ```
   Add the following line to schedule system monitoring every 3 hours
   ```
   0 */3 * * * /usr/local/bin/system-monitor.sh
   ```
7. To create a cron job that reboots the machine at 3 am every Monday, create a shell script
   ```
   sudo nano /usr/local/bin/reboot-logger.sh
   ```
   Add the following code
   ```
   #!/bin/bash
   LOG_FILE="/var/log/reboot.log"
  
   # Log the current date and time of reboot
   echo "Reboot triggered at: $(date)" >> $LOG_FILE
  
   # Reboot the system
   /sbin/reboot
   ```
   Make the script executable
   ```
   sudo chmod +x /usr/local/bin/reboot-logger.sh
   ```
   open the crontab file
   ```
   crontab -e
   ```
   Add the following line to reboot the system at 3 am every Monday
   ```
   0 3 * * 1 /usr/local/bin/reboot-logger.sh
   ```
8. To verify results, check the logs. For malware scan logs use
   ```
   cat /var/log/deep-malware-scan.log
   ```
   For system monitoring logs
   ```
   cat /var/log/system-monitor.log
   ```
   For reboot logs, check the log after the scheduled time
   ```
   cat /var/log/reboot.log
   ```
9. To verify schedule tasks, list all the cron jobs to ensure they are set up
   ```
   crontab -l
   ```
   






   
