# Lab Setup: Deploy A Virtual Machine in AWS
Amazon Web Services (AWS) is a cloud platform that provides on-demand computing power, storage, and other resources. AWS offers a wide variety of services, including virtual machines (VMs). AWS VMs are essentially self-contained computers that run in the cloud. You can create and delete VMs at any time, and you can choose from a wide variety of operating systems and software configurations. AWS VMs are also highly scalable, so you can quickly ramp up or down your computing power as needed. AWS VMs are a great way to quickly get up and running with a cloud-based computer. As an IT system administrator, you will often be required to deploy virtual machines both locally and in the cloud.


## Specifications 
- Register an account on Amazon Web Services (AWS)
- Create and deploy an Ubuntu VM using Amazon EC2


## Benchmarks
- Demonstrate that you can SSH into the VM


## Practical Approach
1. Register an account on AWS. For daily tasks, it is recommended to use an IAM account instead of a root account
2. In AWS, search for EC2 and select it and launch the instance <br>
   ![image](https://github.com/user-attachments/assets/1182c26c-3224-4569-9370-6576e213ecd5)

3. Give a descriptive name <br>
   ![image](https://github.com/user-attachments/assets/f30bebc5-182d-4b40-9eff-83e59bcd9c9a)

4. Select Ubuntu OS from the available OS selections <br>
   ![image](https://github.com/user-attachments/assets/d596a2b3-6915-4fdb-a39b-c88da56cb594)

5. Leave the instance type as default. For the sake of simplicity, select a created key pair <br>
   ![image](https://github.com/user-attachments/assets/efa1e299-2485-4aa1-ad3e-29c7ab35665c)

6. Leave the network settings as default too. The only port of interest is the SSH port <br>
   ![image](https://github.com/user-attachments/assets/0607fc6c-a795-409c-b06c-7ef3adb1b10f)

7. Lastly, leave the storage configuration as it is, because we will not be installing or downloading applications or files with large size <br>
   ![image](https://github.com/user-attachments/assets/b3102307-be07-48ed-88df-ffeb54d4583e)

8. After checking that all configurations are correct, launch the instance <br>
   ![image](https://github.com/user-attachments/assets/60dcf635-cb50-40da-bd09-175be5a5e97e)
 
9. Go to the list of available instances and right click on the created instance and click `Connect` <br>
   ![image](https://github.com/user-attachments/assets/55562f0f-5139-4f62-913a-9a773c028ea5)

10. Navigate to SSH client and copy the ssh command with the details <br>
    ![image](https://github.com/user-attachments/assets/ab5d5542-182b-4879-8743-28d3d3a94899)

11. Launch a linux terminal and run the copied command. The SSH should be successful if the key pair is correctly located <br>
    ![image](https://github.com/user-attachments/assets/ea597144-3ad2-4969-b75e-954fb37ff85e)











