# Deploying a Highly Available Nginx Web Server with SSL and Server Health Monitoring on AWS

Project Overview 

This project sets up a high availability (HA) web infrastructure that includes:
- **Two backend servers:** These was use for serving simple HTML.
- **An NGINX reverse proxy/load balancer** This is used to distribute traffic between the backend servers.
- **SSL encryption** Used  Let’s Encrypt for secure communication.
- **A status page** to monitor server health and active backend server status.

This infrastructure ensures a scalable, secure, and reliable web setup.

## Prerequisites

- **Domain Name**: You must have a domain, such as `sehindemitech.co.uk` hosted .
- **DNS Management**: Route 53 for DNS configuration and management.
- **VM Instances**: 3 virtual machines (VMs) in AWS.
- **NGINX**: Basic understanding of NGINX for configuring the reverse proxy and load balancer.
- **SSL Provider**: Let’s Encrypt or another SSL provider for HTTPS configuration.

## Architecture Overview

### 1. **Domain & DNS Setup**
- **Primary Domain**: `sehindemitech.co.uk`
- **Subdomains**:
  - `app.sehindemitech.co.uk`: Points to the load balancer (for the main web app).
  - `status.sehindemitech.co.uk`: Points to the status page for monitoring server health.

### 2. **Infrastructure Setup**
- **Backend Servers**: Two VM instances running a simple web app (NGINX serving different content).
- **Reverse Proxy/Load Balancer**: A third VM running NGINX configured as a reverse proxy to distribute traffic between the backend servers.

### 3. **SSL Configuration**
- Used **Let’s Encrypt** (or another SSL provider) to secure `app.sehindemitech.co.uk` with HTTPS.
- Enforce **HTTP to HTTPS** redirection to ensure all traffic is encrypted.

### 4. **Status Page & Health Checks**
- **Status Page**: A simple page hosted at `status.sehindemitech.co.uk` that shows:
  - Health of both backend servers (using a script or cURL for checking).
  - The active backend server that’s currently handling requests.

## How to Set It Up

### 1. **Domain & DNS Configuration**
- **Set up your domain**: Ensure that your domain `sehindemitech.co.uk` is managed through **Route 53**.
- **Create subdomains**:
  - **app.sehindemitech.co.uk**: Point this to your load balancer.
  - **status.sehindemitech.co.uk**: Point this to your status page.

### 2. **Deploy Infrastructure**

#### Backend Servers
1. **Create two VM instances** (on AWS or Azure).
2. **Install NGINX** on each backend server.
3. Serve a basic web page (using NGINX) with different content on each server.

#### Reverse Proxy / Load Balancer
1. **Create a third VM instance** to run NGINX as the reverse proxy/load balancer.
2. **Configure NGINX** to distribute incoming traffic between the two backend servers using round-robin or any other preferred method.

### 3. **SSL Configuration**
1. **Install SSL**:
   - Use **Let’s Encrypt** to secure `app.sehindemitech.co.uk` with HTTPS.
   - You can use the `certbot` tool to obtain and install SSL certificates.
2. **Enforce HTTPS**:
   - Configure NGINX to automatically redirect HTTP traffic to HTTPS to ensure all traffic is encrypted.

### 4. **Status Page & Health Checks**

1. **Set up the status page** at `status.sehindemitech.co.uk`:
   - This page should display:
     - Health status of both backend servers.
     - The currently active backend server (you can use a basic script with cURL to check the status of the servers).
   
2. **Health Check Script**:
   - Use a script or cURL to check the health of the backend servers. Display the current active server on the status page.

---
**Heres is what it will look like once done**
![Screenshot 2025-04-02 153705](https://github.com/user-attachments/assets/281f6c02-bd4a-4ef0-af25-87c9520f77a0)
![Screenshot 2025-04-02 153736](https://github.com/user-attachments/assets/77af98e8-7b05-4d50-a1fb-67c5e5a7c837)
![Screenshot 2025-04-02 153923](https://github.com/user-attachments/assets/23bb3b5b-4bf6-427a-b2a2-3e866d9fd08e)

## Useful Links
- [Let’s Encrypt](https://letsencrypt.org/) – Free SSL certificates.
- [NGINX Documentation](https://nginx.org/en/docs/) – Guide to NGINX configuration.

---
