# Simple HTML Website Hosted on AWS EC2

## Overview

This project demonstrates how to create and host a simple static HTML website on an **Amazon EC2 instance** running **Amazon Linux 2023**. The website is served using the **Apache HTTP Server**.

## Technologies Used

- HTML5
- Apache HTTP Server
- Amazon EC2
- Amazon Linux 2023
- Git & GitHub

## Project Structure

```text
project/
├── index.html
└── README.md
```

## Prerequisites

- AWS Account
- Amazon EC2
- Amazon Linux 2023 AMI
- Security Group with HTTP (Port 80) enabled
- SSH client
- Git & GitHub (optional)

# Step 1: Create an EC2 Instance

1. Log in to the **AWS Management Console**.
2. Search for **EC2**.
3. Click **Launch Instance**.
4. Enter an instance name.
5. Under **Application and OS Images**, select:
   - **Amazon Linux 2023**
6. Select an appropriate instance type such as:
   - `t2.micro` or `t3.micro`
7. Create or select an existing **Key Pair**.
8. Under **Network settings**, configure the Security Group.
9. Allow the following inbound rules:

| Type | Protocol | Port |
|------|----------|------|
| SSH | TCP | 22 |
| HTTP | TCP | 80 |

10. Keep the remaining settings as default.
11. Click **Launch Instance**.

## Step 2: Connect to the EC2 Instance

After the instance reaches the **Running** state, copy its **Public IPv4 Address**.

Connect using SSH:

```bash
ssh -i your-key.pem ec2-user@<EC2-PUBLIC-IP>
```

## Step 3: Switch to Root User

After connecting to the EC2 instance, switch to the root user:

```bash
sudo su
```

The command prompt should change to something similar to:

```text
[root@ip-xxx-xxx-xxx-xxx ~]#
```

## Step 4: Install Apache HTTP Server

Install Apache using:

```bash
yum install -y httpd
```

This installs the Apache HTTP Server on the EC2 instance.

## Step 5: Start Apache

Start the Apache service:

```bash
systemctl start httpd
```

## Step 6: Enable Apache at Boot

Enable Apache so that it automatically starts when the EC2 instance is restarted:

```bash
systemctl enable httpd
```

## Step 7: Create the Website

Move to the Apache web directory:

```bash
cd /var/www/html
```

Create the HTML file:

```bash
nano index.html
```

Add your HTML website code inside `index.html`.

For example:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Website</title>
</head>
<body>

    <h1>Welcome to My Website</h1>

    <p>This website is hosted on an Amazon EC2 instance.</p>

</body>
</html>
```

Save the file in Nano:

- Press `Ctrl + O`
- Press `Enter`
- Press `Ctrl + X`

## Step 8: Restart Apache

Restart Apache to make sure the website is served correctly:

```bash
systemctl restart httpd
```

## Step 9: Check Apache Status

Verify that Apache is running:

```bash
systemctl status httpd
```

You should see:

```text
Active: active (running)
```

Press `q` to exit the status screen.

## Step 10: Access the Website

Copy the **Public IPv4 Address** of your EC2 instance.

Open a web browser and enter:

```text
http://<EC2-PUBLIC-IP>
```

For example:

```text
http://3.XXX.XXX.XXX
```

The HTML website should now be displayed in the browser.

## Deployment Process

The deployment process is:

```text
Create EC2 Instance
        ↓
Select Amazon Linux 2023
        ↓
Configure Security Group
        ↓
Connect using SSH
        ↓
sudo su
        ↓
yum install -y httpd
        ↓
systemctl start httpd
        ↓
systemctl enable httpd
        ↓
cd /var/www/html
        ↓
nano index.html
        ↓
systemctl restart httpd
        ↓
Open EC2 Public IP
        ↓
Website Hosted Successfully
```

## Important Commands

```bash
sudo su
yum install -y httpd
systemctl start httpd
systemctl enable httpd
cd /var/www/html
nano index.html
systemctl restart httpd
systemctl status httpd
```

## Security Group Configuration

The EC2 Security Group must allow HTTP traffic.

```text
Inbound Rules

SSH   → TCP → 22 → Your IP
HTTP  → TCP → 80 → 0.0.0.0/0
```

Port **80** is required so that users can access the website through a browser.

## Result

The static HTML website was successfully deployed on an **Amazon EC2 instance running Amazon Linux 2023** and served using the **Apache HTTP Server**. The website can be accessed through the EC2 instance's public IPv4 address.

## Future Enhancements

- Add CSS styling
- Add JavaScript functionality
- Configure a custom domain
- Enable HTTPS using SSL/TLS
- Automate deployment using GitHub Actions
- Configure a reverse proxy

## Conclusion

This experiment demonstrates how to launch an Amazon EC2 instance, install and configure Apache HTTP Server, create an HTML webpage, and host the website using the EC2 public IP address.
