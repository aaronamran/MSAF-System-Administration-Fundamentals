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
   This shows details about the CPU, including model name, cores and clock speed
2. To view memory information, use
   ```
   cat /proc/meminfo
   ```
   This displays information about total memory, free memory, buffers and cache
3. To get a quick overview of memory usage, use
   ```
   free -h
   ```
4. To report system performance including CPU, memory and I/O activity, use
   ```
   vmstat 2 5
   ```
   where 2 is the interval in seconds between updates, and 5 is the number of updates
5. To display a real-time, interactive view of system processes and resource usage, use
   ```
   top
   ```
6. `htop` is an enhanced version of `top` with a better user interface
   ```
   htop
   ```
   
   
