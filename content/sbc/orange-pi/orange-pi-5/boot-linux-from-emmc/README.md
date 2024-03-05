<center>

![logo](/assets/images/logo.svg)

</center>

<center> 

# **Configuring Orange Pi 5 series: Boot Linux from eMMC !!!**

</center>

<div align="center">

![Badge](https://badgen.net/github/license/kaveh-kaviani/tutorials?color=red)
![Badge](https://badgen.net/github/forks/kaveh-kaviani/tutorials?icon=git&color=blue)
![Badge](https://badgen.net/github/watchers/kaveh-kaviani/tutorials?icon=awesome&color=green)
![Badge](https://badgen.net/github/stars/kaveh-kaviani/kaveh-kaviani?icon=graphql&color=blue)
![Badge](https://badgen.net/github/commits/kaveh-kaviani/tutorials?icon=graphql&color=red)

</div>


<br>

# Table of Contents

- [**Configuring Orange Pi 5 series: Boot Linux from eMMC !!!**](#configuring-orange-pi-5-series-boot-linux-from-emmc-)
- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Stages](#stages)
  - [Stage 1: Flushing the SPI Flash](#stage-1-flushing-the-spi-flash)
  - [Stage 2: Preparing the eMMC](#stage-2-preparing-the-emmc)
    - [Stage 2.1: eMMC Sectors Alignment](#stage-21-emmc-sectors-alignment)
  - [Stage 3: Update the Bootloader](#stage-3-update-the-bootloader)
  - [Stage 4: Burn the Linux image on to the eMMC Disk](#stage-4-burn-the-linux-image-on-to-the-emmc-disk)
- [Conclusion](#conclusion)

<br>

<br>

<br>

# [Introduction](#introduction)

<font color="red" size="5" face="roboto"> **This tutorial made before Orange Pi release model 5B and 5 Pro and due to the changes directly regard to the SPI Flash and eMMC in these models, methods in this tutorial will not work on Orange Pi 5 [for more information](/content/sbc/orange-pi/orange-pi-5/README.md). Just for Orange Pi 5B and 5 Pro only those who have eMMC storage and no SPI Flash you may need to skip the first stage and go directly to the [second stage](#stage-2-preparing-the-emmc).** </font>

<font color="white" size="5" face="roboto"> <center> **This tutorial was tested on Orange Pi 5 Plus successfully.** </center> </font>

The Orange Pi 5 series offers several methods to boot from the eMMC. However, not all of these methods are reliable due to the role of the SPI Flash memory, which is responsible for selecting between the SD Card, eMMC, and NVMe as the boot storage.

In this tutorial, we will guide you through the process of booting the Orange Pi 5 series from the eMMC. Specifically, we will focus on the method that involves **burning the linux image directly to the eMMC**. This method has proven to be effective and reliable, making it a great choice for those who want to leverage the speed and durability of eMMC storage.

Please note that this tutorial is based on the official Orange Pi 5 series image, which can be downloaded from the  [official website](http://www.orangepi.org/html/serviceAndSupport/index.html). The official image is a pre-configured image that includes the necessary drivers and software for the Orange Pi 5 series. Therefore, it is recommended to use the official image, as you may encounter booting issues with other images.

This tutorial assumes that you have already installed a bootable Linux image on the SD Card. If you have not done so, please refer to the official documentation for your specific Linux distribution.

# [Prerequisites](#prerequisites)

For this tutorial, you will need the following:
  - **An Orange Pi 5 series board**
  - **A SD Card with a bootable Linux image (e.g., Armbian, Debian, Ubuntu, etc.)** [Please refer to the official documentation of the Orange Pi 5 series board](http://www.orangepi.org/orangepiwiki/index.php/Orange_Pi_5)
  - **An eMMC module (e.g., 64GB, 128GB, 256GB, etc.)**
  - **A power supply that can provide sufficient power (e.g., 5V/3A)**
  - **A cooling system (e.g., heatsink, fan, etc.) to prevent overheating**
  - **Familiarity with the Linux command line interface (CLI)**

<br>

<div align="center">

<font color="red"> **Please Keep in mind, whenever you decied to change the OS on Orange Pi 5 series, you need to delete all the SPI Flash's partitions and update the bootloader** </font>

</div>

_________________

# [Stages](#stages)

The process of booting the Orange Pi 5 series from the eMMC involves several stages. In this section, I will guide you through each stage, providing detailed instructions and explanations.

**Please note that repeating the process of booting from the eMMC may be necessary if you encounter any issues. Therefore, it is important to follow the instructions carefully and be patient, amount of repeating the process depends on the user's experience and the quality of the eMMC module and the SD Card.**

## [Stage 1: Flushing the SPI Flash](#stage-1-flushing-the-spi-flash)

The first stage involves flushing the SPI Flash, which is responsible for selecting the boot storage. By flushing the SPI Flash, we can ensure that the Orange Pi 5 series will boot from the eMMC instead of the SD Card.

To flush the SPI Flash, please follow these steps:

1. **Power off the Orange Pi 5 series board** by disconnecting the power supply.
2. **Install the eMMC module** into the eMMC slot on the Orange Pi 5 series board.(<font color="red"> **please refer to the official documentation of the Orange Pi 5 series board.** </font>)
3. **Insert the SD Card** with the bootable Linux image into the SD Card slot.
4. **Connect the power supply** to the Orange Pi 5 series board.
5. **Power on the Orange Pi 5 series board** by connecting the power supply.
6. **Wait for the Orange Pi 5 series board to boot** from the SD Card.
7. **Log in as the root user** using the default username and password (e.g., orangepi/orangepi).
8. **Open a terminal** on the Orange Pi 5 series board.
9. **Run the following command** to flush the SPI Flash:

<br>

Check the name and current status of the SPI Flash:

```bash
sudo fdisk -l
```
<br>

![Check the name and current status of the SPI Flash](/content/sbc/orange-pi/orange-pi-5/boot-linux-from-emmc/images/01.png)

**The SPI Flash size in OPI 5 series is 16 MB** The Disk which has 16 MiB for example: **/dev/mtdblock0** is the SPI Flash.

<br>

Select the SPI Flash:

```bash
sudo apt install gdisk

sudo gdisk /dev/mtdblock0
```

<br>

For the Command: (you can use ? for help) follow the steps below: (e.g., type `?` and press `Enter` to see the available commands)

1. **Print the Partitions table:**

    type `p` and press `Enter` to see the available commands

2. Delete the Partitions 1 by 1: (you need to Delete all the Partitions)
  
    2.1. **Delete the Partition 1:**

    type `d` and press `Enter` to see the available commands

    type `1` and press `Enter` to see the available commands

    2.2. **Delete the Partition 2:**

    type `d` and press `Enter` to see the available commands

    type `2` and press `Enter` to see the available commands

    <font color="red"> **Note: If you have more than 2 partitions, you need to delete all of them.** </font>

3. **Write table to disk and exit:**

    type `w` and press `Enter` to see the available commands

    type `y` and press `Enter` to see the available commands

    <font color="red"> **Note: Sometimes you need to repeat confirmation 2 times by asking correct this problem? (Y/N):** </font>

**The SPI Flash has been flushed successfully.**

<br>

## [Stage 2: Preparing the eMMC](#stage-2-preparing-the-emmc)

The second stage involves preparing the eMMC which includes deleting all the partitions.

Check the name and current status of the eMMC:

```bash
sudo fdisk -l
```

<br>

![Check the name and current status of the eMMC](/content/sbc/orange-pi/orange-pi-5/boot-linux-from-emmc/images/01.png)

**The eMMC size may vary based on the user's choice** The Disk which has 256 (232.96 GB) for example: **/dev/mmcblk1** is the eMMC.

<br>

<div align="center">

<font color="red"> **Please note that if you don't see the eMMC, you need to check the connection of the eMMC module.** </font>

<font color="red"> **If your eMMC module has no partition, you can skip this stage and move to the next stage [stage 2.1](#stage-2.1-emmc-sectors-alignment).** </font>

</div>

Select the eMMC:

```bash
sudo gdisk /dev/mmcblk1
```

<br>

For the Command: (you can use ? for help) follow the steps below: (e.g., type `?` and press `Enter` to see the available commands)

1. **Print the Partitions table:**

    type `p` and press `Enter` to see the available commands

2. **Delete the Partitions 1 by 1:** (you need to Delete all the Partitions)
  
    2.1. **Delete the Partition 1:**

    type `d` and press `Enter` to see the available commands

    type `1` and press `Enter` to see the available commands

    2.2. **Delete the Partition 2:**

    type `d` and press `Enter` to see the available commands

    type `2` and press `Enter` to see the available commands

    <font color="red"> **Note: If you have more than 2 partitions, you need to delete all of them.** </font>

3. **Write table to disk and exit:**

    type `w` and press `Enter` to see the available commands

    type `y` and press `Enter` to see the available commands

    <font color="red"> **Note: Sometimes you need to repeat confirmation 2 times by asking correct this problem? (Y/N):** </font>

<br>

### [Stage 2.1: eMMC Sectors Alignment](#stage-2.1-emmc-sectors-alignment)

The eMMC sectors alignment is a crucial step that ensures the eMMC is properly aligned and the boot drive will be recognized by the Orange Pi 5 series board. To align the eMMC sectors, please follow these steps:

<div align="center">

<font color="red"> **Note: You may think that the eMMC is already aligned, specially in the example below, but keep in mind the eMMC in the example below it has boot partition and it has been aligned through the burned image on the eMMC process automatically.** </font>

</div>

<br>

```bash
sudo gdisk /dev/mmcblk1
```

<br>

For the Command: (you can use ? for help) follow the steps below: (e.g., type `?` and press `Enter` to see the available commands)

1. **Print the Partitions table:**

    type `p` and press `Enter` to see the available commands

    **Note: If in the descriptions above the Partitions table for the Main partition table begins at sector 2 and ends at 33 and First usable sector is any number <font color="red"> **except** </font> the number after the end of the Main partition's sector in this case 34 for example 2048: then you need to reformat the sectors first before writing the partitions table on the Disk and for that please follow the steps below and if the First usable sector is the number after the end of the Main partition's sector in this case 34, just skip this steps and jump to stage [stage 3](#write-table-to-disk-and-exit).**

    <br>

    ![eMMC Sectors Alignment](/content/sbc/orange-pi/orange-pi-5/boot-linux-from-emmc/images/02.png)
    
    <br>

    type `x` and press `Enter` to move to Expert Command (? for help)

2. **Move the main partition table:**

    type `j` and press `Enter` to move to the Main partition table

    2.1. **Reformat the sectors:**

      It will ask you to Enter new starting location:
    
      type `2` and press `Enter` to see the available commands

3. [**Write table to disk and exit:**](#write-table-to-disk-and-exit)

    type `w` and press `Enter` to see the available commands

    type `y` and press `Enter` to see the available commands

    <font color="red"> **Note: Sometimes you need to repeat confirmation 2 times by asking correct this problem? (Y/N):** </font>


## [Stage 3: Update the Bootloader](#stage-3-update-the-bootloader)

This stage involves updating the bootloader to ensure that the Orange Pi 5 series board will boot from the eMMC. This process does through the built-in configuration menu:

```bash
sudo orangepi-config
```

<br>

1. **Select: System → System and security settings**

    ![Select: System → System and security settings](/content/sbc/orange-pi/orange-pi-5/boot-linux-from-emmc/images/03.png)

<br>

2. **Select: Install → Install to/update boot loader**

    ![Select: Install → Install to/update boot loader](/content/sbc/orange-pi/orange-pi-5/boot-linux-from-emmc/images/04.png)

<br>

3. **Select: 7 → Install/Update the bootloader on SPI Flash**

    ![Select: 7 → Install/Update the bootloader on SPI Flash](/content/sbc/orange-pi/orange-pi-5/boot-linux-from-emmc/images/05.png)

<br>

4. **Select: Yes**

    ![Select: Yes](/content/sbc/orange-pi/orange-pi-5/boot-linux-from-emmc/images/06.png)

    <br>

    <font color="red"> **Note: If you see an error, that means your SPI Flash still has some partitions in it and it does not have enough space for creating another one** </font>

    **Note: It will take a few minutes, then you will see Done at the left bottom corner of your screen and you will back to the system settings menu.**


<br>

1. **Select: Firmware → Run apt update & apt upgrade**

    ![Select: OK](/content/sbc/orange-pi/orange-pi-5/boot-linux-from-emmc/images/07.png)
    
    <br>

    <font color="red"> **and reboot after that and please Do not pull out the SD card still you need to Burn the Linux image on to the eMMC Disk.** </font>
    
    - **Do not worry if your linux machine did not boot again, you can repeat these steps as much as your SD card and eMMC Disk handle. (that depends to the quality of your SD card and eMMC Disk)**

      - **If your linux machine did not boot again, just take out the SD card and repeat the process of making a [bootable SD card](http://www.orangepi.org/orangepiwiki/index.php/Orange_Pi_5) and then repeat the process from [stage 3](#update-the-bootloader) to the end of the process.**

<br>

## [Stage 4: Burn the Linux image on to the eMMC Disk](#stage-4-burn-the-linux-image-on-to-the-emmc-disk)

This stage involves burning the Linux image on to the eMMC Disk. For this stage, you will need to use a Linux image that is compatible with the Orange Pi 5 series board. The official Linux image can be downloaded from the [official website](http://www.orangepi.org/html/serviceAndSupport/index.html), and it is recommended to use the official image to avoid any booting issues, please follow these steps:

1. **Download the official Linux image** from the [official website](http://www.orangepi.org/html/serviceAndSupport/index.html).
   
    <font color="red"> **Note: It is important for the image to contains all the boot configurations and Drivers for you Orange Pi model** </font>

<br>

2. **Extract the Linux image** from the downloaded file.

    **Note: Just remember, what ever method you using, please decompress it from .7z or .xz or .gz linux image compressed file.**

<br>

1. **Transfer the Linux image to the Linux machine that you have used to prepare the eMMC (AKA: Orange Pi 5 series board).** (e.g., using a USB flash drive, SSH, WinSCP, etc.)

<br>

4. **Open a terminal** on the Linux machine.

<br>

5. **Move to the directory** where the Linux image is located (e.g., /home/orangepi/Downloads/) using the `cd` command.:

    ```bash
    cd /home/orangepi/Downloads/

    ls
    ```

<br>

6. **Check the path of the eMMC boot disk**:

    ```bash
    ls /dev/mmcblk*boot0 | cut -c1-12
    ```

    <br>

    ![Check the path of the eMMC boot disk](/content/sbc/orange-pi/orange-pi-5/boot-linux-from-emmc/images/08.png)

<br>

7. **Using dd command to burn the Linux image on to the eMMC disk**:

    **Note: In the dd command below, for if= you need just to type the name of the image with the .img extension and it is better if you rename the image file to a short name for example debian.img, for the of= just type the path of the eMMC disk which you retrieve on last step (6) for example: of=/dev/mmcblk0**
    ```bash
    sudo dd bs=1M if=debian.img of=/dev/mmcblk0 status=progress
    ```

    <font color="red"> **Note: This process will take a few minutes, please be patient and do not interrupt the process.** </font>

<br>

1. **Confirm the changes**:

    ```bash
    sudo sync
    ```

<br>

9. **Confirm the result**:

    ```bash
    sudo fdisk -l
    ```

    **Note: In your list you must see the SPI Flash (aka: /dev/mtdblock0 ), SD card (aka: /dev/mmcblk0) and eMMC Disk (aka: /dev/mmcblk1) all have partitions, if yes, then you have done the process successfully.**

<br>

1.  **Power off the Orange Pi 5 series board**:

    ```bash
    sudo poweroff
    ```

    **Note: Please do not pull out the SD card until the system is completely off.**

<br>

# [Conclusion](#conclusion)

In this tutorial, we have guided you through the process of booting the Orange Pi 5 series from the eMMC. Specifically, we have focused on the method that involves burning the Linux image directly to the eMMC. This method has proven to be effective and reliable, making it a great choice for those who want to leverage the speed and durability of eMMC storage.

By following the instructions in this tutorial, you should be able to boot the Orange Pi 5 series from the eMMC without any issues. However, if you encounter any issues, please refer to the official documentation of the Orange Pi 5 series board or seek help from the community.

Thank you for reading this tutorial, and I hope you found it helpful. **We appreciate your following and sharing this tutorial with others who may find it useful and star the repository on GitHub**.

**Author: Kaveh Kaviani**

**------March 2024------**



--------------------