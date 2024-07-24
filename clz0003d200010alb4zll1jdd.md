---
title: "Unlock Extra Storage: Mounting an EBS Volume on Your EC2 Instance"
datePublished: Sat Jul 13 2024 18:30:00 GMT+0000 (Coordinated Universal Time)
cuid: clz0003d200010alb4zll1jdd
slug: unlock-extra-storage-mounting-an-ebs-volume-on-your-ec2-instance
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1721834545549/69d27ca2-bc59-4d95-9bd1-f3d49205f5cc.jpeg
tags: ec2, linux, aws, cloud-computing, devops, ebs, linux-for-beginners, linux-basics, devops-articles, devops-journey, trainwithshubham, volume-mount, tws, devopscommunity

---

# Day 10 - How to Mount a Volume in AWS EC2 Linux: A Beginner's Guide

If you're new to AWS (Amazon Web Services) and working with EC2 (Elastic Compute Cloud) instances, you might need to attach additional storage to your instance at some point. This storage comes in the form of EBS (Elastic Block Store) volumes. In this guide, we'll walk you through the steps to mount a volume to your EC2 Linux instance in simple terms.

## What is an EBS Volume?

Think of an EBS volume as a USB drive for your computer. It's an additional storage device that you can attach to your EC2 instance to store more data. You can detach it and reattach it to another instance if needed.

## Steps to Mount a Volume in AWS EC2 Linux

### 1\. Create and Attach an EBS Volume

1. **Log into AWS Console:**
    
    * Go to [AWS Management Console](https://aws.amazon.com/console/).
        
    * Log in with your credentials.
        
2. **Navigate to EC2 Dashboard:**
    
    * Click on "Services" at the top and then select "EC2" under "Compute."
        
3. **Create a New Volume:**
    
    * In the left-hand menu, click on "Volumes" under the "Elastic Block Store" section.
        
    * Click the "Create Volume" button.
        
    * Specify the size, type, and Availability Zone (make sure it's the same zone as your EC2 instance).
        
    * Click "Create Volume."
        
4. **Attach the Volume to Your EC2 Instance:**
    
    * After the volume is created, right-click on the volume and select "Attach Volume."
        
    * Choose your instance from the list and click "Attach."
        

## 2\. Connect to Your EC2 Instance

1. **Open a Terminal:**
    
    * If you're on Windows, you might use PuTTY. On macOS or Linux, you can use the terminal.
        
2. **Connect to Your EC2 Instance:**
    
    * Use the following command to connect (replace `your-key.pem` with your key file and `ec2-user@your-instance-public-dns` with your instance details):
        
        ```bash
        ssh -i your-key.pem ec2-user@your-instance-public-dns
        ```
        

### 3\. Mount the EBS Volume

1. **List Attached Disks:**
    
    * Once logged in, list all attached disks with:
        
        ```bash
        lsblk
        ```
        
    * You should see a new disk (e.g., `xvdf` or `nvme1n1`) that wasn't there before.
        
2. **Create a Filesystem on the Volume:**
    
    * Format the new volume to prepare it for use. Replace `xvdf` with your actual device name:
        
        ```bash
        sudo mkfs -t ext4 /dev/xvdf
        ```
        
3. **Create a Mount Point:**
    
    * Create a directory where you will mount the volume:
        
        ```bash
        sudo mkdir /mnt/mydata
        ```
        
4. **Mount the Volume:**
    
    * Mount the volume to the directory:
        
        ```bash
        sudo mount /dev/xvdf /mnt/mydata
        ```
        
5. **Verify the Mount:**
    
    * Check if the volume is mounted correctly:
        
        ```bash
        df -h
        ```
        
    * You should see your new volume listed with its mount point.
        

### 4\. (Optional) Make the Mount Permanent

To ensure the volume is mounted automatically after a reboot:

1. **Edit the fstab File:**
    
    * Open the fstab file with a text editor like `nano`:
        
        ```bash
        sudo nano /etc/fstab
        ```
        
    * Add the following line at the end (replace `xvdf` and `/mnt/mydata` with your actual device name and mount point):
        
        ```bash
        /dev/xvdf /mnt/mydata ext4 defaults,nofail 0 2
        ```
        
2. **Save and Exit:**
    
    * Save the file and exit the editor (in `nano`, press `Ctrl+X`, then `Y`, and `Enter`).
        

## Conclusion

That's it! You've successfully mounted an EBS volume to your AWS EC2 Linux instance. Now you can use this additional storage for your applications or data. Remember, if you ever stop or terminate your instance, the data on the EBS volume will remain intact, but you'll need to remount it if you start a new instance.

Happy cloud computing!