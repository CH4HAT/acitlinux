# ACIT 2420 Assignment 1 - Fall 2024

### Learning Objectives:
This tutorial will teach you how to use ‘doctl’ and a cloud-init configuration to setup and operate a remote server on DigitalOcean. You can automate the setup of new droplets with this configuration.

### Prerequisites:
- Existing Arch Linux droplet:  this tutorial will also give a brief about how to create a droplet using DigitalOcean web Console.
- SSH key pair: you need ssh keypair to securely access the droplets.

### Introduction:
In this tutorial, we will be creating a Droplet running Arch Linux using the ‘doctl’ command-line tool. we will use ‘doctl’ and cloud-init for every step of setting up the Arch Linux droplet. We will start by manually setting up an Arch Linux droplet and will automate the process using ‘doctl’ and cloud-init configuration.

### Steps on creating Arch Linux droplet using DigitalOcean web console:

### 1. Generate SSH key pair on your local Machine
Open terminal and run the command below to create SSH key pair:
```
ssh-keygen -t ed25519 -f ~/.ssh/your-key -C “your-email”
```
This will create two keys: 
   - your-key 
   - your-key pub (this is the public key you will use to connect to your DigitalOcean account)
### 2. Add your public key to DigitalOcean:
- Login to your DigitalOcean account 
- In the navigation bar on the left Click Settings -> Security -> SSH keys.
- Paste your public key here (The key you just created)

![DigitalOcean SSH keys](assents/ssh_do.png)

#### 3. Create an Arch Linux Droplet:
In the DigitalOcean web console:
- Click the **Create** button and select **Droplet**.
- Choose the **Custom Image** tab and upload your Arch Linux image(the “qco” file you downloaded).
- Set the region and data center (e.g., **SFO3**).
- Choose an appropriate CPU option (e.g., **$7 AMD**).
- Under **Authentication**, select **SSH Key** and add the key you uploaded.
- Set a hostname for your droplet (change it to something simple) (e.g., **arch-droplet**).
- Click **Create Droplet** and note the IP address of your new droplet.

#### 4. Connect to Your Droplet via SSH:
Use the command below to connect to your droplet:
```
ssh -i ~/.ssh/your-key username@your-droplet-IPaddress
```

