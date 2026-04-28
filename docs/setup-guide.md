# Setup Guide

## FTP Log Analysis and Threat Detection Using Splunk

This guide explains how to set up the environment for the IT 360 Final Project: FTP Log Analysis and Threat Detection Using Splunk.

---

## Required Tools

- Splunk Enterprise (Free Trial Version)
- FTP Server (FileZilla Server or vsftpd)
- GitHub
- Windows or Linux Virtual Machine
- Sample FTP Log File

---

## Step 1: Install Splunk

### Download Splunk

1. Go to the official :contentReference[oaicite:0]{index=0} website
2. Download **Splunk Enterprise Free Trial**
3. Choose your operating system:
   - Windows (.msi)
   - Mac (.dmg)
   - Linux (.tgz or .rpm)

### Install Splunk

1. Run the installer
2. Follow installation steps
3. Create admin username and password
4. Complete installation

### Start Splunk

Open browser and go to:

```text
http://localhost:8000
Step 2: Prepare FTP Log File
Create a sample FTP log file named:

sample_ftp_logs.log
Example content:

2026-04-01 10:15:32 LOGIN FAILED user=admin ip=192.168.1.10
2026-04-01 10:18:01 LOGIN SUCCESS user=john ip=192.168.1.15
2026-04-01 10:18:45 FILE UPLOAD user=john file=project1.zip
2026-04-01 10:19:20 FILE DOWNLOAD user=mary file=report.pdf
Save this file inside the project folder:

logs/sample_ftp_logs.log
Step 3: Upload Logs into Splunk
Open Splunk Home

Click Add Data

Select Upload

Click Select File

Choose:

sample_ftp_logs.log
Configuration
Source Type: Custom (ftp_logs)

Host: Default

Index: Default (main)

Click:

Review → Submit
This imports the FTP logs into Splunk.

Step 4: Verify Log Ingestion
Go to:

Search & Reporting
Run:

index=main
Change the time range to:

All Time
This should display all uploaded FTP log events.

Step 5: Detection Queries
Failed Login Detection
index=main "LOGIN FAILED"
| rex "user=(?<user>\S+)"
| rex "ip=(?<ip>\S+)"
| stats count by user ip
| sort - count
Purpose:
Detect repeated failed login attempts by user and IP address.

Brute Force Detection
index=main "LOGIN FAILED"
| rex "ip=(?<ip>\S+)"
| stats count by ip
| where count >= 5
| sort - count
Purpose:
Identify brute force attacks from repeated failed login attempts.

File Activity Monitoring
index=main ("FILE UPLOAD" OR "FILE DOWNLOAD" OR "FILE DELETE")
| rex "user=(?<user>\S+)"
| rex "file=(?<file>\S+)"
| stats count by user file
Purpose:
Monitor suspicious file uploads, downloads, and deletions.

Step 6: Create Dashboard
Go to:

Dashboards → Create New Dashboard
Dashboard Information
Title:

FTP Security Monitoring Dashboard
Type:

Classic Dashboard
Add Panels
Create 3 panels using:

Failed Login Detection

Brute Force Detection

File Activity Monitoring

Visualization Type:

Statistics Table
This creates a centralized monitoring dashboard.

Step 7: Create Alert
Run:

index=main "LOGIN FAILED"
| rex "ip=(?<ip>\S+)"
| stats count by ip
| where count >= 5
Click:

Save As → Alert
Alert Configuration
Title:

FTP Brute Force Alert
Type:

Scheduled
Trigger Condition:

Number of Results > 0
Action:

Add to Triggered Alerts
This creates an automatic alert for brute force attack detection.
