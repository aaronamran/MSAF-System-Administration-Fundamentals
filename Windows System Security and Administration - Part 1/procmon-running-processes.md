# Use Procmon To View, Analyze And Monitor Running Processes On A Windows Machine
Process Monitor is a tool on the Windows system that helps you monitor system activities. You can view registry, filesystem, process and network activity in real-time

## References
- [Process Monitor v4.01](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon) by Mark Russinovich on Microsoft

## Tasks
- Capture procmon events for a few minutes
- Use procmon filters and display events for 'cmd.exe' and 'powershell.exe'
- Determine the registry keys queried by the process 'explorer.exe'
- Filter out file 'READ' events
- Save all the events to a CSV file


## Practical Approach
1. Download and launch `Procmon.exe` as admin. It will start capturing events automatically. Let it run for a few minutes <br/>
   ![image](https://github.com/user-attachments/assets/b8bea60c-9bc7-42d2-babf-1e5d5e102ea7)

2. Press `Ctrl + L` or click on the Filter menu and choose Filter....
3. Set up filters and include events for `Process Name` is `cmd.exe` and `powershell.exe`. Click Add after each condition, then OK to apply the filters <br/>
   ![image](https://github.com/user-attachments/assets/1104fd40-0797-47fa-bc28-06247fc44055)

4. To analyse registry keys queried by `explorer.exe`, clear the previous filters by going to Filter and Reset Filter. To set a new filter, set `Process Name` as `explorer.exe` and click Add, then OK <br/>
   ![image](https://github.com/user-attachments/assets/6f5e0ca5-9b12-4dc5-bf1c-b57da69c5aaa)

5. In the `Path` column, look for entries that start with `HKCU\` (HKEY_CURRENT_USER) or `HKLM\` (HKEY_LOCAL_MACHINE) to find queried registry keys
6. To see details about the registry query, right-click on any event and select `Properties` <br/>
   ![image](https://github.com/user-attachments/assets/16aa07ac-9ea1-499a-9b7f-f92e46149c50)

7. To filter out file 'READ' events, add another filter using `Operation is not READFILE`, click Add then OK <br/>
   ![image](https://github.com/user-attachments/assets/e38398da-47ec-4930-8a1e-482c55128a0b)

8. To save events, press `Ctrl + S` or go to File > Save.... Then select All Events or Filtered Events depending on what is needed. Choose the CSV format <br/>
   ![image](https://github.com/user-attachments/assets/95314799-0edf-4f99-a802-d33e66c395a1)

   
