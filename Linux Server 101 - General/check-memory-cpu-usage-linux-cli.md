# Check The Memory Usage And CPU Usage On A Linux Machine Using Command Line Utilities


## Tasks
- Use the following command-line Linux utilities to analyze the memory and CPU usage:
  - cat
  - free
  - vmstat
  - top
  - htop
 

## Practical Approach
1. To view CPU information, use
   ```
   cat /proc/cpuinfo
   ```
   This shows details about the CPU, including model name, cores and clock speed <br/>
   ![image](https://github.com/user-attachments/assets/64eaac48-7fce-48b8-971d-d0060f69e5b4)

2. To view memory information, use
   ```
   cat /proc/meminfo
   ```
   This displays information about total memory, free memory, buffers and cache <br/>
   ![image](https://github.com/user-attachments/assets/a4c98c35-eb20-4135-b690-b286fb9cd919) <br/>
   ![image](https://github.com/user-attachments/assets/aaa4a5b4-812d-410b-b18d-ca3a6e840017)


3. To get a quick overview of memory usage, use
   ```
   free -h
   ```
   ![image](https://github.com/user-attachments/assets/f0f5843c-2b19-4998-b925-bc50f065243f)
   Output:
   - total, used, free: Memory statistics
   - shared: Memory shared among processes
   - cache/buffer: Memory used for caching and buffering
   - available: Memory available for new processes.


5. To report system performance including CPU, memory and I/O activity, use
   ```
   vmstat 2 5
   ```
   where 2 is the interval in seconds between updates, and 5 is the number of updates <br/>
   ![image](https://github.com/user-attachments/assets/fd6dc3b5-3810-403b-bc86-30c4f6ec5235)
   - r: Processes waiting for CPU
   - free: Free memory
   - buff: Memory used as buffers
   - si/so: Swap in/out activity
   - cpu (us, sy, id): User, system, and idle CPU percentages

7. To display a real-time, interactive view of system processes and resource usage, use
   ```
   top
   ```
   ![image](https://github.com/user-attachments/assets/95c49ebc-7484-4f25-9088-fbb47fe50765)

8. `htop` is an enhanced version of `top` with a better user interface
   ```
   htop
   ```
   ![image](https://github.com/user-attachments/assets/5e3e1b8c-5374-4a05-99b5-ca529d0ede4a)

   
