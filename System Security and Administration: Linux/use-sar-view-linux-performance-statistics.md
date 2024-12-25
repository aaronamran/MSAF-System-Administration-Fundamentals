# Use System Activity Reporter (SAR) To View Performance Statistics Of A Linux System
System Activity Reporter (SAR) is part of the SYSSTAT utilities, which is a collection of performance monitoring tools for Linux. SAR collects CPU usage and statistics, used and available memory, overall I/O activities of the system, etc. It helps system administrators to monitor Linux systems effectively


## References
- [How to use sar for monitoring your Linux system? sysstat sar examples and usage](https://www.blackmoreops.com/2014/06/18/sysstat-sar-examples-usage/) by blackMORE OPS


## Tasks
- Install and launch a Linux VM
- Install and configure System Activity Reporter (SAR)
- Using SAR, list CPU usage of all CPUs
- List CPU usage of individual CPU or Core
- List free and used memory
- List overall I/O activities
- List all network statistics



## Practical Approach
1. For this task, Lubuntu VM is used
2. To install and configure SAR, run the following commands
   ```
   sudo apt update && sudo apt install sysstat -y
   ```
3. Edit the configuration file to enable SAR logging
   ```
   sudo nano /etc/default/sysstat
   ```
   Change `ENABLED="false"` to `ENABLED="true"` and save and exit
4. Restart the SYSSTAT service
   ```
   sudo systemctl restart sysstat
   ```
5. Verify SAR installation using
   ```
   sar -V
   ```
   ![image](https://github.com/user-attachments/assets/831e1542-ac7b-4004-811c-f662d6b9d28d)

6. To list CPU usage of all CPUs, use
   ```
   sar -u 1 3
   ```
   `-u` reports CPU usage, `1` collects data every second, `3` reports for three intervals <br/>
   ![image](https://github.com/user-attachments/assets/c104011f-c713-4429-b72d-55ae5f4c1c84)

7. To list CPU usage of individual CPU or core, use
   ```
   sar -P ALL 1 3
   ```
   `-p ALL` shows statistics for each CPU core <br/>
   ![image](https://github.com/user-attachments/assets/2be5fc3b-2dd9-4289-b2c5-001ff9c0d5bd)

8. To list free and used memory, use
   ```
   sar -r 1 3
   ```
   `-r` reports memory usage. The output includes free, used, and buffered memory <br/>
   ![image](https://github.com/user-attachments/assets/dcd79261-7255-4bb3-9d64-7bfb8428073f)

9. To list overall I/O activiites, use
   ```
   sar -b 1 3
   ```
   `-b` reports block device activity (I/O stats) <br/>
   ![image](https://github.com/user-attachments/assets/632f52b6-5660-443b-a059-06683b850e47)

10. To list all network statistics, use
    ```
    sar -n ALL 1 3
    ```
    `-n ALL` displays all network statistics, including packets sent/received and errors <br/>
    ![image](https://github.com/user-attachments/assets/1f6b2fd8-e98b-402f-b5f5-fd1446cd18e8)

11. SAR logs are stored in `/var/log/sysstat/`. To save the SAR logs, use the `sar` command with a date to view specific logs
    ```
    sar -f /var/log/sysstat/sa<DD>
    ```
    replace `<DD>` with the day of the month





