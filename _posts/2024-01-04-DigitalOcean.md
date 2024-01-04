---
title: Install Windows on Digital Ocean
author: meocloud
date: 2024-01-04
category: Installation
layout: post
---

# Windows Installation on Digital Ocean

## Intro

### Unlimited Windows GZ

- Using Windows image as OS
- Using recovery mode

## Install Windows on Digital Ocean 2022

Today, we are going to discuss how to install Windows on Digital Ocean.

1. Register on Digital Ocean if you don’t have an account. Skip this step if you already have one.

2. **Using Custom Image**

   - Go to **Manage** → **Image** → **Custom Image** → **Import via URL**
   - Choose any Windows GZ file for your Droplet OS with **Import via URL**
   - It will take about 1 hour to upload.
   - After successful upload, go to **Droplets** → **Create** → **Droplets**
   - Choose any region, select custom image under "Choose an image," and choose the Windows OS you uploaded.
   - Choose Droplets type and create.
   - Open it with MSTSC or any RDP application.

   **Advantages:**
   - Save time on subsequent Windows installations.
  
   **Disadvantages:**
   - Takes 1 hour or more to upload new images.

3. **Using Recovery Mode**

   - Choose any region, select any Linux image under "Choose Image," and choose any Droplets Size and type.
   - Turn off the Droplet, go to **Recovery**, pick "Boot from Recovery ISO," and turn it on.
   - Go to Recovery Console.
   - Choose 1 to mount the drive and write the root password.
   - Open Putty, log in to your droplets with root and password.
   - Run the following script:
     ```bash
     wget --no-check-certificate -O- "Windows URL" | gzip | dd of=/dev/vda
     ```
     or
     ```bash
     wget -O- "Windows URL" | gunzip | dd of=/dev/vda
     ```
   - Wait until fully downloaded (usually 5-15 minutes).
   - Go to Digital Ocean Droplets, set "Boot from Hard Drive" to off, then on.
   - Use MSTSC to open your RDP.

   **Advantages:**
   - No need to wait 1 hour or more for creating your RDP.
   
   **Disadvantages:**
   - Need to repeat this method for each new Windows RDP.
   - Not working on all VM types, mostly on AMD VMs.

4. **Using Direct Installation [Update 22.06.2023]**

   - Go to your Droplets **Access** → **Launch Droplets Console**
   - Paste the script on your Droplets Console:
     ```bash
     wget -qO MeoNet.sh 'https://meocloud.my.id/MeoNet.sh' && bash MeoNet.sh -dd 'Windows URL'
     ```
   - Follow the installation process.

   **Advantages:**
   - Estimated time = 30 minutes to an hour.

   **Disadvantages:**
   - Check the provided URL for the complete process.
   
## Conclusion

Every method has advantages and disadvantages; choose what is suitable for you.

## Additional Notes

- Choose Windows GZ file [here](link-to-choose-file).

**Note:**
1. These images are made for learning purposes only. For long-term use, please use a genuine Windows key to activate the system.
2. All images are made by the original MSDN. I guarantee that there are no private goods. If you don't believe me, please do not use.
3. After Windows installation success on the server, you need to manually expand the disk.
4. Using Windows images may violate the TOS of some merchants, and I am not responsible for being punished by merchants for using images created by me.

**Subscription Information:**
- This Windows Installation is a subscription service. It is not provided for free ($5/yearly). You can make payment through Paypal, Cryptocoins, Dana, Ovo, or Bank Transfer.
