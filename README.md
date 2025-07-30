# jenkins-installation

# 🚀 Install Jenkins on Ubuntu EC2 Instance (AWS)

This guide walks you through installing **Jenkins** on an **Ubuntu-based EC2 instance**.

---

## 📋 Prerequisites

- AWS EC2 instance (Ubuntu 20.04 or 22.04 LTS recommended)
- SSH access to the instance
- Security Group with:
  - ✅ Port 22 (SSH)
  - ✅ Port 8080 (Jenkins)

---

## 🖥️ Step 1: Connect to EC2 via SSH

```bash
ssh -i your-key.pem ubuntu@your-ec2-public-ip
Replace your-key.pem and your-ec2-public-ip with your actual key and instance IP.
```
☕ Step 2: Install Java (Jenkins requirement)
```bash
sudo apt update
sudo apt install openjdk-11-jdk -y
```
📦 Step 3: Install Jenkins
```bash
# Add Jenkins GPG key
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null

# Add Jenkins repository
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

# Update and install Jenkins
sudo apt update
sudo apt install jenkins -y
```
▶️ Step 4: Start Jenkins
```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```
Check status:
```bash
sudo systemctl status jenkins
```
🌐 Step 5: Open Jenkins in Your Browser
Visit:
```bash
http://<your-ec2-public-ip>:8080
Make sure port 8080 is open in your EC2 security group.
```
🔑 Step 6: Unlock Jenkins
Get the initial admin password:
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
Copy the password and paste it into the Jenkins web interface.
```
✅ Step 7: Complete Jenkins Setup

  Install suggested plugins

  Create admin user
  Start building!

