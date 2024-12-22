# Documentation for Cloud Project

## Public IP Address and URL
- **Public IP Address**: [34.226.205.11](34.226.205.11)
- **Domain**: [chukwuweta.chickenkiller.com](http://chukwuweta.mooo.com)

## Screenshot
Include a screenshot showing your HTML page in a browser. (Add this screenshot to the repository.)

---

## Step-by-Step Guide

### 1. Provisioning the Server
#### Steps to Provision the Server:
1. Log in to your AWS account.
2. Navigate to the EC2 dashboard and launch a new instance.
3. Choose the following configuration:
   - **AMI**: Ubuntu Server 20.04 LTS.
   - **Instance Type**: t2.micro (free tier eligible).
   - **Key Pair**: Create or select an existing key pair for SSH access.
   - **Security Group**: Allow the following ports:
     - SSH (port 22)
     - HTTP (port 80)
     - HTTPS (port 443).
4. Launch the instance and note the public IPv4 address.

#### Connect to the Server:
```bash
ssh -i your-key.pem ubuntu@34.226.205.11
```

### 2. Installing the Web Server
#### Install Nginx:
```bash
sudo apt update
sudo apt install -y nginx
```
#### Start and Enable Nginx:
```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

### 3. Deploying the HTML Page
#### Create the HTML Page:
1. Navigate to the web root directory:
   ```bash
   cd /var/www/html
   ```
2. Create the HTML file:
   ```bash
   sudo nano index.html
   ```
3. Add the following content of your choice (Sample content below):
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <title>Welcome to Chukwuweta's Landing Page</title>
   </head>
   <body>
       <h1>Welcome to Chukwuweta's Landing Page</h1>
       <p>This project demonstrates my skills as part of my cloud engineering program.</p>
       <h2>About Me</h2>
       <p>Chukwuweta Mitchel Okonjo, aspiring cloud and DevOps engineer with experience in web development and system administration.</p>
   </body>
   </html>
   ```
4. Save and exit (Ctrl+O, Enter, Ctrl+X).

#### Adjust Permissions (if necessary):
```bash
sudo chown www-data:www-data /var/www/html/index.html
sudo chmod 644 /var/www/html/index.html
```

### 4. Configuring Networking
#### Allow HTTP and HTTPS Traffic:
1. Update the instance security group to allow traffic on ports 80 (HTTP) and 443 (HTTPS).
2. Verify the firewall settings:
   ```bash
   sudo ufw allow 'Nginx Full'
   sudo ufw enable
   sudo ufw status
   ```

---

## Repository Structure
```
repository/
├── README.md   # Documentation (this file)
├── screenshot.png   # Screenshot of the HTML page
└── index.html  # Deployed HTML page
```
