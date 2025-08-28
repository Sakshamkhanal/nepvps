---
title: "How to Use SSH to Connect to a Remote Server"
date: 2023-07-24
author: "Michael Park"
description: "Learn how to securely connect to a remote server using SSH, including step-by-step instructions for Linux, macOS, and Windows."
categories: ["Tutorials"]
tags: ["SSH", "Remote Access", "Linux", "macOS", "Windows"]
featured_image: "/images/blog/ssh.jpg"
---

{{< toc >}}

## Introduction

Secure Shell (SSH) is a cryptographic network protocol that enables secure communication between a client and a server. It's commonly used for remote administration of servers. This guide will walk you through the process of connecting to a remote server using SSH.

## Prerequisites

Before you begin, ensure you have the following:

- A terminal application:
  - **Linux/macOS**: Terminal
  - **Windows**: PowerShell, Git Bash, or Windows Subsystem for Linux (WSL)
- The server's IP address
- A user account on the server (e.g., `root` or another user)
- Authentication credentials:
  - **Password**: The user's password on the server
  - **SSH Key**: A private SSH key if key-based authentication is set up

## Connecting to the Server

### Step 1: Open Your Terminal

- **Linux/macOS**: Launch the Terminal application.
- **Windows**: Open PowerShell, Git Bash, or WSL.

### Step 2: Run the SSH Command

Use the following command to initiate an SSH connection:

```bash
ssh username@server_ip
```

Replace `username` with your server's username and `server_ip` with the server's IP address. For example:

```bash
ssh root@192.168.1.100
```

### Step 3: Accept the Host Key

The first time you connect to a server, you'll be prompted to accept its host key:

```
The authenticity of host '192.168.1.100 (192.168.1.100)' can't be established.
ECDSA key fingerprint is SHA256:xyz123abc456.
Are you sure you want to continue connecting (yes/no)?
```

Type `yes` to proceed. This step ensures you're connecting to the correct server and helps prevent man-in-the-middle attacks.

### Step 4: Authenticate

Depending on your server's configuration, you'll either:

- **Enter your password**: Type your password when prompted.
- **Use SSH keys**: If key-based authentication is set up, the system will authenticate you automatically.

### Step 5: You're Connected!

Once authenticated, you'll have access to the server's command line. You can now execute commands on the remote server.

To exit the SSH session, type:

```bash
exit
```

## Troubleshooting Tips

- **Permission Denied**: Ensure you're using the correct username and password or that your SSH key is properly configured.
- **Host Key Verification Failed**: If you receive this error, the server's host key may have changed. Verify the server's identity before proceeding.
- **Connection Timeout**: Check your network connection and ensure the server's firewall allows incoming SSH connections on port 22.

## Conclusion

SSH provides a secure and efficient way to manage remote servers. By following the steps outlined in this guide, you can establish a secure connection to your server and perform administrative tasks remotely.

For more detailed information, refer to the original DigitalOcean tutorial: [How to Use SSH to Connect to a Remote Server](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-to-connect-to-a-remote-server).
