# Cloud Lab 1 — Amazon EC2

- **Student Name:** Peng Seyha
- **Student ID:** e20220620
- **Learner Lab Username:** `voclabs/user5623008=PENG_SEYHA`
- **Date:** October 30, 2026

---

## Part 1.1 — Amazon EC2 Walkthrough

### 1. Security Group

Created `aws-bootstrap-security-group` with SSH (22) and HTTP (80) inbound rules.

![Security Group](images/01-security-group.png)

### 2. Key Pair

Created `aws-bootstrap-key-pair` using RSA and downloaded the `.pem` file.

![Key Pair](images/02-key-pair.png)

### 3. EC2 Instance

Launched an EC2 instance with Amazon Linux 2023, `t2.micro`, and 8 GiB storage.

![EC2 Instance](images/03-instance-details.png)

### 4. Browser Test

Opened the public IP in a browser and successfully displayed the Hello World page.

![Browser Test](images/04-browser-test.png)

### 5. SSH Connection

Connected to EC2 using SSH from my Ubuntu terminal and verified the connection using `whoami` and `hostname`.

![SSH Connection](images/05-ssh-connection.png)

---

## Part 1.2 — EC2 Web Solution Challenge

### 1. Launch Configuration

Created a Linux EC2 instance using `t2.micro` with a 10 GiB root volume.

![Launch Configuration](images/06-challenge-launch.png)

### 2. Security Group

Configured SSH (22) and HTTP (80) inbound rules.

![Security Group](images/07-challenge-security-group.png)

### 3. Running Instance

Launched the challenge instance successfully.

![Running Instance](images/08-challenge-instance.png)

### 4. Web Server Installation

Installed Apache and created the webpage using these commands:

```bash
sudo dnf install -y httpd
sudo systemctl start httpd
sudo systemctl enable httpd
sudo systemctl status httpd --no-pager

echo "Welcome to the EC2 Challenge" | sudo tee /var/www/html/index.html

cat /var/www/html/index.html
curl http://localhost
```

**Result:**

```text
Welcome to the EC2 Challenge
```

![Terminal Commands](images/09-challenge-terminal.png)

### 5. Browser Test

The webpage worked locally, but the public IP connection timed out. This step was not completed.

---
