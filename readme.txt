Activity 1:

Create two directories named Current and other in your Linux machine using the command “mkdir Current” and “mkdir Other”.
Navigate to Current Directory using the command “cd Current”
Create a new Hello World Program in python in the Current directory. Use the command “nano name.py”. here I have used the Sahil.py. Once you hit the enter, editor will open up where you can code the script.
Note: Save the script using the ctrl + s and exit the editor using the ctrl + x.
4. Make the script executable using the command “chmod +x Sahil.py”. and verify it by running it using “./Sahil.py”.

Adding Program to $PATH
Method 1: Temporarily

Modify the $PATH in the current directory.
Run the following command in the terminal “export PATH=$PATH:~/Current” and verify it by running the python file.
Go the OTHER Directory (use the command ls to make sure this directory is empty) and run the script
Restart the VM to check if the script is temporary or not.
After Restarting the VM, once your run the script, it will show not found.
Method 2: Permanent
9. Run the command “nano /.bashrc”
• A new editor will open up.
• Go to end of the script and type “export PATH=$PATH:/Current”

Source the file to apply change using the command “source ~/.bashrc”
Restart the Machine.
Verify Permanent Path
Note: Added to $PATH permanently.






Activity 2:

• Install the Apache Web server using the command “sudo apt install apache2”

• Go to “tmp” directory in the system using the terminal and paste the GitHub repository of your web page using the “git clone” command or you can write your own HTML file (I used my existing portfolio repository which not only highlights my achievements but also serves as an online resume).
• And then copy the repository using the “cp” command to “/var/www/html”
• To verify if the file is copied or not, you can go to “/var/www/html” directory and check using nano command.
• Give the read permissions to the directory /var/www/html.
• As shown below.

• Type the command, “sudo nano /etc/hosts” and give the domain as “127.0.0.1 sahil.local”, as shown below.
• Here we provide the local IP Address of the server 1 with the domain name.

• Go to your Browser, and type the domain name.
• Here I entered the “sahil.local” and it showed me the my portfolio webpage.
• In the following screenshots, I have attached all the images of my web page.

• Go to terminal and check the IP of the server 1 and write it down.

• Go to terminal of another VM, Here I have used ubuntu as second VM( you can choose windows as well).
• Go to “/etc/hosts/” and type the IP address of the first VM (which is 192.168.196.137 in my case) along with the domain of the website(which is sahil.local in my case). Save the file.

• To verify if the connection is settled, you can check using the ping command with the domain name.

• Go to your Browser of 2nd VM and type the domain name.
• Here I entered the “sahil.local” and it showed me the my portfolio webpage.



Activity 3: 


Step 1: Add the Hard Disk
Open the virtual machine settings (e.g., VirtualBox or VMware).
Add a new hard disk:
Go to Storage settings.
Select Add New Hard Disk and choose the desired size.
Save the settings and restart the VM.
Step 2: Check the New Disk
After booting, verify the new disk is added:
bash
Copy code
ls /dev/
Look for the new disk (e.g., /dev/sdb).
Step 3: Partition the Disk
Open fdisk to manage the disk:

bash
Copy code
sudo fdisk /dev/sdb
Inside fdisk:

Create Partition 1:
Press n → select Primary → choose 1 → allocate size.
Create Partition 2:
Press n → select Primary → choose 2 → allocate size.
Create Partition 3:
Press n → select Primary → choose 3 → allocate remaining size.
Save the changes by pressing w.
Verify the partitions:

bash
Copy code
sudo fdisk -l /dev/sdb
You should see /dev/sdb1, /dev/sdb2, and /dev/sdb3.

Step 4: Create a File System
Format the entire disk as ext3:
bash
Copy code
sudo mkfs -t ext3 /dev/sdb
Step 5: Verify the File System
Confirm file system creation:
bash
Copy code
df -h /dev/sdb
It will show the disk usage and confirm the file system is active.
