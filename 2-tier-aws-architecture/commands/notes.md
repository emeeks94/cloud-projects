# Ontario Events - Build Notes & Commands

> These are the primary commands used while building the AWS two-tier architecture. They are documented for reproducibility and future reference.

---

# Clone the Project

```bash
git clone https://github.com/<your-username>/ontario-event-finder.git
cd ontario-event-finder
```

---

# Install Project Dependencies

```bash
npm install
```

---

# Build the Frontend

```bash
npm run build
```

---

# Verify Build Output

```bash
ls -la
ls -la .output/
find .output/public -maxdepth 2 -type f
```

---

# Connect to EC2 via AWS Systems Manager

Session Manager was used instead of SSH because the EC2 instance was deployed in a private subnet with no public IP.

---

# Update the Server

```bash
sudo dnf update -y
```

---

# Install nginx

```bash
sudo dnf install nginx -y
```

---

# Enable nginx

```bash
sudo systemctl enable nginx
```

---

# Start nginx

```bash
sudo systemctl start nginx
```

---

# Check nginx Status

```bash
sudo systemctl status nginx
```

---

# Verify HTTP Response

```bash
curl http://localhost
```

Expected output:

```
Ontario Events Backend
Healthy
```

---

# Edit the Default nginx Page

```bash
sudo nano /usr/share/nginx/html/index.html
```

---

# Restart nginx

```bash
sudo systemctl restart nginx
```

---

# Verify Network Configuration

Check the instance IP address.

```bash
ip addr
```

---

# Verify Listening Ports

```bash
sudo ss -tulpn
```

---

# AWS Console Tasks

The following resources were configured through the AWS Management Console:

- Created a custom VPC
- Created Public and Private Subnets
- Configured Internet Gateway
- Configured NAT Gateway
- Created Route Tables
- Created Security Groups
- Launched EC2 Instance
- Attached IAM Role for Session Manager
- Created Target Group
- Configured Application Load Balancer
- Uploaded static site to Amazon S3
- Configured CloudFront Distribution
- Configured Origin Access Control (OAC)
- Added `index.html` as CloudFront Default Root Object
- Created S3 Lifecycle Policy
- Validated ALB Health Checks

---


