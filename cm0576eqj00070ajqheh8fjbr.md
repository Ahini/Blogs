---
title: "Get Your GitHub On – The Easy Way!"
datePublished: Thu Aug 22 2024 11:26:37 GMT+0000 (Coordinated Universal Time)
cuid: cm0576eqj00070ajqheh8fjbr
slug: get-your-github-on-the-easy-way
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1724325885003/bea7192e-f984-42ca-8b80-e68963c60076.jpeg
tags: github, git, devops, ssh, devops-articles, devops-trends, devops-journey, ssh-git, personal-access-tokens, devopscommunity

---

# Day 13 - Connecting GitHub to Your Local Machine with PAT and SSH

## Introduction

So, you've started your coding journey and are ready to collaborate on projects, share your work, or just keep your code organized on GitHub. But how do you connect your local machine (your computer) to GitHub so that you can push and pull code easily? Don’t worry, I’ve got you covered! In this guide, we’ll walk through the two popular methods to connect GitHub with your local account: using a Personal Access Token (PAT) and SSH keys. Let's dive in!

> Note: These methods below are the followed IT industry standards

## Method 1: Connecting GitHub with Personal Access Token (PAT)

### What is PAT?

A Personal Access Token (PAT) is like a password that gives your local machine permission to access your GitHub account securely.

### Steps to Connect Using PAT

1. **Generate a PAT on GitHub:**
    
    * Go to GitHub and log in to your account.
        
    * Click on your profile picture in the top right corner, then select **Settings**.
        
    * In the left sidebar, click on **Developer settings**.
        
    * Under **Personal access tokens**, click on **Tokens (classic)**.
        
    * Click on **Generate new token**.
        
    * Give it a name, select the scopes (permissions) you need, and then click **Generate token**.
        
    * Copy the token somewhere safe because you won’t see it again.
        
2. **Set Up Git Locally:**
    
    * Open your terminal (or Command Prompt on Windows).
        
    * Set your GitHub username:
        
        ```bash
        git config --global user.name "YourGitHubUsername"
        ```
        
    * Set your GitHub email:
        
        ```bash
        git config --global user.email "your-email@example.com"
        ```
        
3. **Clone a Repository Using Your PAT:**
    
    * In GitHub, navigate to the repository you want to clone.
        
    * Click on the **Code** button and copy the HTTPS URL.
        
    * In your terminal, run the following command, replacing `yourPAT` with the token you generated and `repositoryURL` with the URL you copied:
        
        ```bash
        git clone https://yourPAT@github.com/YourUsername/YourRepository.git
        ```
        
    * When prompted for a password, paste your PAT.
        
4. **Push and Pull with PAT:**
    
    * Now, you can push and pull code using Git commands like `git push` and `git pull` without being asked for your username or password.
        

## Method 2: Connecting GitHub with SSH

### What is SSH?

SSH (Secure Shell) keys allow you to securely connect to GitHub without needing to enter your username and password every time.

### Steps to Connect Using SSH

1. **Generate an SSH Key:**
    
    * Open your terminal.
        
    * Generate a new SSH key by typing:
        
        ```bash
        ssh-keygen -t ed25519 -C "your-email@example.com"
        ```
        
    * When prompted, choose a location to save the key (press Enter to save it in the default location).
        
    * Set a passphrase if you want extra security, or press Enter to leave it empty.
        
2. **Add Your SSH Key to the SSH Agent:**
    
    * Start the SSH agent in the background:
        
        ```bash
        eval "$(ssh-agent -s)"
        ```
        
    * Add your SSH private key to the SSH agent:
        
        ```bash
        ssh-add ~/.ssh/id_ed25519
        ```
        
3. **Add Your SSH Key to GitHub:**
    
    * Copy your SSH key to your clipboard:
        
        ```bash
        cat ~/.ssh/id_ed25519.pub | pbcopy
        ```
        
    * Go to GitHub, click on your profile picture, and go to **Settings**.
        
    * In the left sidebar, click **SSH and GPG keys**.
        
    * Click on **New SSH key**, give it a title, and paste your key into the "Key" field.
        
    * Click **Add SSH key**.
        
4. **Clone a Repository Using SSH:**
    
    * In GitHub, go to the repository you want to clone.
        
    * Click on the **Code** button and copy the SSH URL.
        
    * In your terminal, type:
        
        ```bash
        git clone git@github.com:YourUsername/YourRepository.git
        ```
        
5. **Push and Pull with SSH:**
    
    * Now you can push and pull code without needing to enter your credentials!
        

## Conclusion

That’s it! You’re now connected to GitHub using either PAT or SSH, making it easier than ever to manage your code. Whether you’re a solo coder or collaborating on a team, these methods ensure that your workflow is smooth and secure. Happy coding!