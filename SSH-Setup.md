# SSH Setup

```
wget -O /home/apps/SD-Web-Refactored/public/adminer.php https://www.adminer.org/latest.php

vi ~/.ssh/config
mkdir ~/.ssh/keys/ ; mv ~/Downloads/LightsailDefaultKey-us-west-2.pem ~/.ssh/keys
ls ~/.ssh/keys/
cd ~/.ssh/keys/
ls
ll -h
chmod 600 LightsailDefaultKey-us-west-2.pem
ll
chmod 600 LightsailDefaultKey-us-west-2.pem
ll
ssh ms
```

# File Upload Procedure

## Overview

This document provides a step-by-step procedure for uploading a file to a remote server using **SCP** (Secure Copy Protocol) from your local machine.

## Prerequisites

- SSH access to the server.
- SSH private key configured on your machine (if applicable).
- SCP command installed on your local machine.

## Steps to Upload a File

### Step 1: Open Terminal/Command Prompt

- **Windows**: Open **PowerShell** or **Git Bash**.
- **Mac/Linux**: Open the **Terminal**.

### Step 2: Check if SCP is Installed

Run the following command to ensure **SCP** is installed:

```
scp -V
```

### Setup 3: Remove exist Old backup

```
rm -rf build.bak build.zip
```

### Setup 4: Upload file

- If You upload from local computer

```
scp -i "C:\Users\dell\Downloads\SmartDoko\LightsailDefaultKey-us-west-2.pem" "C:\Users\dell\Downloads\build.zip" bitnami@44.242.67.85:/home/bitnami/ms-dev/quiz-frontend
scp -i ~/.ssh/keys/ms_ec2.pem "C:\Users\dell\Downloads\build.zip" ubuntu@34.219.184.223:/home/skincare.ktmlabs.com/quiz-frontend
scp -i ~/.ssh/keys/ms_ec2.pem "C:\Users\dell\Downloads\build.zip" ubuntu@34.219.184.223:~
```

- If you upload from hosted url

```
wget -O 'build.zip' 'https://cdn.discordapp.com/attachments/1206908369143603210/1305750564499357767/build.zip?ex=67342a7a&is=6732d8fa&hm=443db52c865cb47ae2cde408812a3b543f7700b92e4b4f8d75aab267af2af92d&'
```

### Setup 5: Keep Backup file of old file

```
mv build build.bak ; unzip build.zip
```
```
upload_max_filesize = 10M
post_max_size = 20M
max_execution_time = 300
max_input_time = 300
memory_limit = 256M
```

# ngrok http 80 --host-header=inventory-management.test
# /usr/bin/php8.1 /usr/bin/composer update


python manage.py shell

<!-- change password -->
from django.contrib.auth.models import User

user = User.objects.get(username='rabin@ktmlabs.com')
user.set_password('loc@lP@ssword')
user.save()

print("Password updated successfully.")

<!-- cache clear -->
from django.core.cache import cache
cache.clear()

sudo service supervisor restart