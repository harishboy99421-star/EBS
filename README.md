# EBS
EBS -
## Aim
To create and configure an Amazon Elastic Block Store (EBS) volume, attach and mount it to an Amazon EC2 instance, create a snapshot backup, and restore the snapshot to a new EBS volume.

## Algorithm / Steps
Create a new Amazon EBS volume with a size of 1 GiB.

Select the same Availability Zone as the EC2 instance.

Attach the EBS volume to the EC2 instance using /dev/sdb.

Connect to the EC2 instance using AWS Systems Manager Session Manager.

Check the available storage using df -h.

Create an ext3 file system on the EBS volume.

Create the /mnt/data-store directory.

Mount the EBS volume to /mnt/data-store.

Configure /etc/fstab for automatic mounting.

Verify that the EBS volume is successfully mounted.

Create file.txt inside the mounted EBS volume.

Verify the contents of the created file.

Create an EBS snapshot named My Snapshot.

Delete file.txt from the original EBS volume.

Create a new EBS volume from the snapshot.

Attach the restored volume to the EC2 instance using /dev/sdc.

Create the /mnt/data-store2 directory.

Mount the restored volume to /mnt/data-store2.

Verify that file.txt has been successfully restored.

Program
1. Check Available Storage
df -h
2. Create an ext3 File System
sudo mkfs -t ext3 /dev/sdb
3. Create a Mount Directory
sudo mkdir /mnt/data-store
4. Mount the EBS Volume
sudo mount /dev/sdb /mnt/data-store
5. Configure Automatic Mounting
echo "/dev/sdb   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
6. View the File System Configuration
cat /etc/fstab
7. Verify the Mounted Volume
df -h
8. Create a File in the EBS Volume
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
9. Read the File
cat /mnt/data-store/file.txt
10. Delete the File
sudo rm /mnt/data-store/file.txt
11. Verify File Deletion
ls /mnt/data-store/
12. Create a Mount Directory for the Restored Volume
sudo mkdir /mnt/data-store2
13. Mount the Restored EBS Volume
sudo mount /dev/sdc /mnt/data-store2
14. Verify Snapshot Restoration
ls /mnt/data-store2/


<img width="1920" height="1080" alt="Screenshot (14)" src="https://github.com/user-attachments/assets/9b322ab3-e5c4-4dc7-af09-04a2ac0647f9" />
<img width="1920" height="1080" alt="Screenshot (15)" src="https://github.com/user-attachments/assets/d1b73bba-6464-46d3-b23d-730c901c14cd" />
<img width="1920" height="1080" alt="Screenshot (16)" src="https://github.com/user-attachments/assets/0b581ae4-799e-4c92-a0d8-56c4428a8521" />

<img width="1920" height="1080" alt="Screenshot (30)" src="https://github.com/user-attachments/assets/af6b6973-d64f-4f5a-978e-a74fbca48fd9" />
<img width="1920" height="1080" alt="Screenshot (32)" src="https://github.com/user-attachments/assets/a43916be-32be-43fb-82c6-f020489d9cf0" />
<img width="1920" height="1080" alt="Screenshot (33)" src="https://github.com/user-attachments/assets/2d34bfbd-391d-4525-aa8e-42f0e2c3436f" />
<img width="1920" height="1080" alt="Screenshot (34)" src="https://github.com/user-attachments/assets/cf647eb9-4a86-45d3-a40f-ecdb0391f93e" />

<img width="1920" height="1080" alt="Screenshot (35)" src="https://github.com/user-attachments/assets/031bfcce-741b-4ac8-a180-1fd6dd6ebc38" />

<img width="1920" height="1080" alt="Screenshot (36)" src="https://github.com/user-attachments/assets/64b6bc38-09e2-4bd0-b220-11f6fc1f5734" />
<img width="1920" height="1080" alt="Screenshot (37)" src="https://github.com/user-attachments/assets/e183aaf1-c67c-449e-83ea-b2a572b003c1" />
<img width="1920" height="1080" alt="Screenshot (38)" src="https://github.com/user-attachments/assets/2cca05c3-2426-49c0-9928-00c1fa10a338" />
## Result
 View the File System Configuration Verify the Mounted Volume
