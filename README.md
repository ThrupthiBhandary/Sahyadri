# Simple HTML Website Hosted on AWS EC2

## Overview

This project is a simple static website developed using HTML and hosted on an Amazon EC2 instance running Amazon Linux 2023. The website is served using the Apache HTTP Server.

## Features

- Simple and responsive HTML webpage
- Hosted on AWS EC2
- Apache Web Server configuration
- Accessible through the EC2 public IP address

## Technologies Used

- HTML5
- Apache HTTP Server
- Amazon EC2
- Amazon Linux 2023
- Git & GitHub

## Project Structure

```
project/
├── index.html
└── README.md
```

## Prerequisites

- AWS Account
- EC2 Instance (Amazon Linux 2023)
- Security Group allowing HTTP (Port 80)
- Git (optional)

## Installation

1. Connect to your EC2 instance.

```bash
ssh -i your-key.pem ec2-user@<EC2-PUBLIC-IP>
```

2. Install Apache.

```bash
sudo dnf install -y httpd
```

3. Start and enable Apache.

```bash
sudo systemctl start httpd
sudo systemctl enable httpd
```

4. Copy the HTML file to the Apache web directory.

```bash
sudo cp index.html /var/www/html/
```

5. Restart Apache.

```bash
sudo systemctl restart httpd
```

## Access the Website

Open your browser and visit:

```
http://<EC2-PUBLIC-IP>
```

## Deployment

The website is deployed on an Amazon EC2 instance using Apache Web Server.

## Future Enhancements

- Add CSS styling
- Add JavaScript for interactivity
- Configure a custom domain
- Enable HTTPS using SSL/TLS
- Automate deployment using GitHub Actions

## Author

**Thrupthi Bhandary**
