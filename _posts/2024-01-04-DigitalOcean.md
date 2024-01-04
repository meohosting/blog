---
title: Install Windows on Digital Ocean
author: meocloud
date: 2024-01-04
category: Installation
layout: post
---

---
title: Install Windows on DigitalOcean
description: What have I done
---

# Install Windows on DigitalOcean

## Table of Contents
- [Intro](#intro)
- [Using Custom Images](#using-custom-images)
- [Advantages and Disadvantages](#custom-image-summary)
- [Using Recovery Mode](#using-recovery-mode)
- [Advantages and Disadvantages](#recovery-mode-summary)
- [Using Direct Installation](#using-direct-installation)
- [Conclusion](#conclusion)
- [Image Link](#image-link)
- [Comments](#comments)

## Intro
Install Windows on DigitalOcean. There are two methods:
1. [Custom Images](#using-custom-images)
2. [Recovery Method](#using-recovery-mode)
3. [Direct Method](#using-direct-installation)

## Using Custom Images
### Video Tutorial
[![Watch the video](https://meocloud.my.id/wp-content/uploads/2023/11/aaaaa-970x527.png)](https://www.youtube.com/embed/jhafqQ3UYp4)

#### Step One
1. Go to **Manage** - **Image** - **Custom image** - Import via URL
   ![Step One Image](https://meocloud.my.id/wp-content/uploads/2022/11/do1.png)

#### Step Two
2. Choose any [Windows GZ file](https://meocloud.my.id/?p=6) for your Droplet OS with Import via URL.
   After the Windows OS is successfully uploaded, go to **Droplets** - **Create** - **Droplets**
   ![Step Two Image](https://meocloud.my.id/wp-content/uploads/2022/11/do2.png)

#### Step Three
3. Choose any **Region** you like.
   On **Choose an image**, choose **custom image**, and select the **Windows OS** you just uploaded.
   ![Step Three Image](https://meocloud.my.id/wp-content/uploads/2022/11/do3.png)

4. Choose **Droplets** type and create.

#### Step Four
5. Open it with **MSTSC** or any Application for RDP.

##### Custom Image Summary
- **Advantages**
  - Save time on the next Windows installation; no need to install every time you make a new droplet.
- **Disadvantages**
  - Takes 1 hour or more to upload new images.

## Using Recovery Mode
Next method is using recovery mode to install Windows on Digital Ocean. This method not working on all VM Type, mostly work on AMD KVM Machine. Choose Premium AMD Machine. So, this is the alternative way, and I am personally not recommended this method.

1. Go to **Droplets** - **Create** - **Droplets**
   ![Step One Image](https://meocloud.my.id/wp-content/uploads/2022/11/do2.png)

2. Choose any **Region** you want, and on **Choose Image** just choose any linux image and choose any **Droplets Size** and type that you want
   ![Step Two Image](https://meocloud.my.id/wp-content/uploads/2022/11/do4.png)

3. **Turn off** the Droplets that you just created and go to **Recovery**, and pick **Boot from Recovery ISO**, and **turn it on**
   ![Step Three Image](https://meocloud.my.id/wp-content/uploads/2022/11/do5.png)

4. Go to **Recovery Console**
   ![Step Four Image](https://meocloud.my.id/wp-content/uploads/2022/11/do6.png)

5. On Recovery Console, Choose **1** to mount the drive and write the root password
   ![Step Five Image](https://meocloud.my.id/wp-content/uploads/2022/11/do7.png)

6. Open **Putty** and login to your droplets with root and password that you just write it down.
   - `sudo su -`
   - `choose 1` (mount disk image)
   - `choose 5` (Attempt to "chroot" into installation system)
   - Paste this script:
     ```sh
     wget --no-check-certificate -O- "Windows URL" | gzip | dd of=/dev/vda
     ```
     or
     ```sh
     wget -O- "Windows URL" | gunzip | dd of=/dev/vda
     ```
   - Wait until it fully downloaded. Usually takes 5-15 minutes until fully download
   ![Step Six Image](https://meocloud.my.id/wp-content/uploads/2022/11/do8.png)

7. After the image fully downloaded, Go to your Digital Ocean Droplets and set **Boot from Hard Drive** - **turn it off** - **turn it on**

8. Use **MSTSC** to open your RDP

##### Recovery Mode Summary
- **Advantages**
  - No need 1 hour or more to create your RDP
- **Disadvantages**
  - You need to do this method every time you create a new droplet.
  - This method is not working on all Droplets.

## Using Direct Installation
1. Go to **Droplets** - **Create** - **Droplets** - Choose Windows OS - Choose any **Region** you want - Choose any **Droplets Type** you like and **Create**
   ![Step One Image](https://meocloud.my.id/wp-content/uploads/2022/11/do2.png)

2. After your Droplets is successfully created, open it with **MSTSC** or any Application for RDP.

3. After your Droplets is on, the next step is to connect to it with **MSTSC** and do the installation.

##### Conclusion
With the Custom Image method, you can save time on the next Windows installation, as you won't need to install it every time you create a new Droplet. However, keep in mind that it takes 1 hour or more to upload new images.

The Recovery Mode method is an alternative way that may not work on all VM types, mostly working on AMD KVM machines. It's not recommended personally due to its limitations.

Direct Installation is the simplest method, where you create a new Droplet with Windows OS directly.

## Image Link
[Windows GZ File](_posts/2024-01-04-WindowsLinks.md)

## Comments
Feel free to share your thoughts or ask questions about the methods described above.
