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

## Level 3 – Creating and Managing droplets using ‘doctl’ and cloud-init
Now you have a running Arch linux machine, you will be creating another droplet in the running Arch linux machine and you will Install and configure `doctl` in an existing droplet(one you have) and use it to create a new droplet.

### 1. Use SSH to get into your existing droplet:
Use the command below:
```
ssh username@your-droplet-IP address
```
Username = the username you gave to your droplet

![SSH key on your Arch Machine](assets/sshkkey_virtual.png)

### 2. Create SSH key pair on your Arch Droplet:
Use the command below:
``` 
ssh-keygen -t ed25519 -C “your-email”
```
Notice that there is not specific path, In Linux it goes to a default location that is “~./.ssh/”
Now copy the content of the key and paste to to your DigitialOcean account as we did before.
To write the content of the public key you use the command below (OpenAI, chatgpt4, 2023):
```
Cat ~/.ssh/id_ed25519.pub
```
