---
title: "Demystifying Linux Commands: SSH, SCP, and Systemctl for Beginners"
datePublished: Fri Jul 12 2024 18:30:00 GMT+0000 (Coordinated Universal Time)
cuid: clyxdibjc000109lb2a945naq
slug: demystifying-linux-commands-ssh-scp-and-systemctl-for-beginners
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/SYTO3xs06fU/upload/94b563c9f5887bf99c3a26f83f22e883.jpeg
tags: linux, devops, linux-for-beginners, linux-basics, devops-articles, linux-commands, devops-trends, devops-journey, 90daysofdevops, 90daysofdevops-chanllenge, 90daysofdevopschallenge, tws, devopscommunity

---

# Day 9 - SSH, SCP and Systemctl

Linux can seem like a complex world with its own language of commands and tools. Three essential tools you will often hear about are SSH, SCP, and Systemctl. Let's break down what these tools are and how you can use them, even if you're just starting out with Linux.

---

## SSH: Secure Shell

### What is SSH?

SSH stands for Secure Shell. It's a method for securely connecting to another computer over a network. Think of it like a secure tunnel through which you can control a remote computer as if you were sitting right in front of it.

### How to Use SSH?

1. **Install SSH**: First, make sure SSH is installed on your computer. Most Linux distributions come with it pre-installed. You can check by typing:
    
    ```bash
    ssh -V
    ```
    
    This will display the version of SSH installed, if any.
    
2. **Connect to a Remote Machine**: To connect to another computer (let's call it a server), you need its IP address or domain name and your login credentials. The basic syntax is:
    
    ```bash
    ssh username@server_address
    ```
    
    For example, if your username is `john` and the server's IP address is `192.168.1.10`, you would type:
    
    ```bash
    ssh john@192.168.1.10
    ```
    
3. **Authenticate**: You'll be prompted to enter your password. Once authenticated, you can execute commands on the remote machine just like on your local computer.
    

## SCP: Secure Copy

### What is SCP?

SCP stands for Secure Copy Protocol. It's a method for securely transferring files between computers using the SSH protocol. Think of it like a secure version of copying files from one place to another.

### How to Use SCP?

1. **Basic File Transfer**: The basic syntax for copying a file from your local computer to a remote server is:
    
    ```bash
    scp /path/to/local/file username@server_address:/path/to/remote/directory
    ```
    
    For example, to copy a file named `example.txt` from your local `Documents` folder to a remote server, you might type:
    
    ```bash
    scp ~/Documents/example.txt john@192.168.1.10:/home/john/
    ```
    
2. **Copy a File from Remote to Local**: To copy a file from the remote server to your local computer, reverse the order:
    
    ```bash
    scp username@server_address:/path/to/remote/file /path/to/local/directory
    ```
    
    For example:
    
    ```bash
    scp john@192.168.1.10:/home/john/example.txt ~/Documents/
    ```
    
3. **Recursive Copy**: To copy entire directories, use the `-r` flag:
    
    ```bash
    scp -r /path/to/local/directory username@server_address:/path/to/remote/directory
    ```
    

## Systemctl: Service Manager

### What is Systemctl?

Systemctl is a command-line utility that allows you to control the systemd system and service manager. It lets you start, stop, enable, and manage services (programs that run in the background).

### How to Use Systemctl?

1. **Check Service Status**: To see if a service is running, use:
    
    ```bash
    systemctl status service_name
    ```
    
    For example, to check the status of the SSH service:
    
    ```bash
    systemctl status ssh
    ```
    
2. **Start a Service**: To start a service (make it run), use:
    
    ```bash
    systemctl start service_name
    ```
    
    For example:
    
    ```bash
    bashCopy codesystemctl start ssh
    ```
    
3. **Stop a Service**: To stop a running service, use:
    
    ```bash
    systemctl stop service_name
    ```
    
    For example:
    
    ```bash
    systemctl stop ssh
    ```
    
4. **Enable a Service**: To configure a service to start automatically at boot time, use:
    
    ```bash
    systemctl enable service_name
    ```
    
    For example:
    
    ```bash
    systemctl enable ssh
    ```
    
5. **Disable a Service**: To prevent a service from starting at boot, use:
    
    ```bash
    systemctl disable service_name
    ```
    
    For example:
    
    ```bash
    systemctl disable ssh
    ```
    

---

## Wrapping Up

SSH, SCP, and Systemctl are powerful tools in the Linux world that can make managing remote computers and services much easier. With SSH, you can securely access remote machines. With SCP, you can securely transfer files between machines. And with Systemctl, you can manage services running on your system.

These tools might seem intimidating at first, but with a bit of practice, you'll find them incredibly useful. Happy Linux-ing!