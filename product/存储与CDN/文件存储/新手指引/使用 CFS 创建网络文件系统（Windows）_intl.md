
## 1. Creating and Configuring a CVM Instance
To access the file system, you need to mount the file system to Linux- or Windows-based Tencent Cloud CVM instances. In this step, you will create and configure a Windows-based Tencent Cloud CVM instance. If you want to use a Linux-based CVM, please see [Creating a Network File System (Linux) with CFS](/doc/product/582/11523). If a CVM instance has been created, go to Step 2 [Create a File System and Mount Point](#1).

Go to the Tencent Cloud official website, select **Cloud Products** -> **Compute and Network** -> **CVM**, then click **Buy Now** to enter the [CVM purchase page](https://buy.cloud.tencent.com/buy/cvm).

### (1) Select a region and model
![](//mc.qcloudimg.com/static/img/3ed8bab8cce3dde578a6e3fb14267ea5/image.png)
- Select a billing mode: Prepaid or postpaid (users who cannot purchase postpaid CVMs need to complete [Identity Verification](https://console.cloud.tencent.com/developer/auth) first). For more information, please see [Billing Mode](/doc/product/213/2180).
- Select a region and an availability zone: When you need more than one CVM, it is recommended that you choose different availability zones to implement disaster recovery.
- Select a model and configuration: For more information, please see [Instance Types](/doc/product/213/7153).

### (2) Select an image
![](//mc.qcloudimg.com/static/img/56c4ecbdb12dd0a366ecf701153fce1d/image.png)
- Select an image provider.
Tencent Cloud supports public images, custom images, shared images and service marketplace images. You can view [Image Types](/doc/product/213/4941) to select an image. The public image type, which contain legitimate Windows operating system, is recommended for users who have just started using Tencent Cloud. You need to build subsequent operating environment on your own.
- Select an operating system: Windows Server.
- Select a system version.

### (3) Select storage and network
![](//mc.qcloudimg.com/static/img/e95a5bf7bf47c60f43dd0ee62946b67a/image.png)
- Select the type of disk and the size of data disk.
Tencent Cloud provides two types of disks, cloud disk and local disk (system disk size is optional. The default is 50 GB).
 - Cloud disk: Deliver high data reliability with the distributed three-copy mechanism.
 - Local disk: A storage device on the physical machine where the CVM resides in, which allows low latency but may cause single point of failure risk. For the comparison, please see [Product Category](/doc/product/362/2353).
- Select a network type.
Tencent Cloud provides two network types: basic network and VPC.
 - Basic network: Suitable for new users. CVMs of the same user are interconnected via the private network.
 - VPC: Suitable for advanced users. Different VPCs are logically isolated from each other.
- Select the public network bandwidth.
Tencent Cloud provides two options: Bill-by-bandwidth or bill-by-traffic.
 - Bill-by-bandwidth: Select a fixed bandwidth. Packet loss occurs if this bandwidth is exceeded. This is suitable for scenarios with minor network fluctuation.
 - Bill-by-traffic: The service is charged based on the actual traffic usage. You can set a limit for peak bandwidth to avoid extra fees caused by unplanned traffic. Packet loss occurs when the instantaneous bandwidth exceeds this limit. This is suitable for scenarios with large network fluctuations.
- Select the quantity.
- Select the usage period and renewal method (only for prepaid CVMs).

### (4) Configure information
![](//mc.qcloudimg.com/static/img/fbc4230b5e6a19ef6ec60ffebfc62aaa/image.png)
- Set CVM name: You can name it after creation or name it now.
- Set login information: You can set a password or use an automatically generated password. The password you set can be modified after creation of CVM. The automatically generated password is sent to you via the internal message.
- Select a security group (**Make sure that the login port 3389 is enabled.** For more information, please see [Security Group](/doc/product/213/5221)).

Click **Buy Now** button to complete the payment before you can log in to the [console](https://console.cloud.tencent.com/cvm) to check your CVM.
After the CVM is created, you will receive an internal message containing such information as instance name, public IP address, private IP address, login name, and initial login password. You can use the information to log in to and manage instances.
 

<span id="1"></span>
## 2. Creating File System and Mount Point

1. Log in to the Tencent Cloud [Console](https://console.cloud.tencent.com/). Click **Cloud Products** -> **Storage** -> **CFS** to go to the CFS console.
![](//mc.qcloudimg.com/static/img/4fee6ea61cfba11927f6891527237610/image.png)

2. In the Tencent Cloud CFS console, click **Create** and the Create File System popup window appears. Enter relevant information and confirm, and then click **OK** to create the file system.
![](https://main.qcloudimg.com/raw/3797c04469bf0da994d2e2876a2a39ad.png)
 - Name: Name the file system to be created.
 - Region and availability zone: Choose a region closest to your customers to minimize access latency and improve download speed.
 - File protocol: NFS (suitable for Linux and Unix clients), CIFS/SMB (suitable for Windows clients).
 - Network type: Tencent Cloud provides two network types: basic network and VPC. Basic network is suitable for new users. CVMs of the same user are interconnected via the private network. VPC is suitable for advanced users. Different VPCs are logically isolated from each other.
  	
 > **Note:**
 > Create and mount a file system based on the network where your CVM instance resides.
 > - To allow a file system to be shared by CVMs under a VPC, you need to select VPC when creating a file system. When the file system belongs to VPC, only CVM instances in the same VPC can be mounted if no specific network settings are made.
 > - To allow a file system to be shared by CVMs under a basic network, you need to select basic network when creating a file system. When the file system belongs to basic network, only CVM instances in the same basic network can be mounted if no specific network settings are made.
 > - For more information on how to share a file system among multiple networks, please see [Cross-availability zone and Cross-network Access to File System](/doc/product/582/9764).

3. Obtain the mount point information. After the file system and the mount point are created, click the instance ID to enter the file system details page, and then click **Mount Point Information** to obtain the mount command for Windows.

The mount point information of NFS file system is as follows:
![](https://mc.qcloudimg.com/static/img/f50435216defb4083874bc78d568001e/image.png)

The mount point information of CIFS/SMB file system is as follows: 
![](https://main.qcloudimg.com/raw/939aafe4bca9907bc391d41e8798c4a6.png)



## 3. Connecting Instances
This section describes how to log in to a Windows CVM. Login method depends on the scenarios. This step shows how to log in to the CVM in the console. For more information on other login methods, please see [Log in to Windows Instance](/doc/product/213/5435).

**Prerequisites**
You need to use the admin account ID and the corresponding password to log in to the CVM.
- Admin account ID: It is Administrator for all Windows instances.
- Password: The password is the one you specified when purchasing the CVM instance.
   
**Log in to CVM via the console**
(1) In the Action column of CVM list, click **Log In** button to connect to Windows CVM via VNC.
![](//mc.qcloudimg.com/static/img/d017c67c9f447c1441cf74ed4ac2b279/image.png)
(2) By sending the **Ctrl-Alt-Delete** command at the top left corner, enter the system login screen.
![](//mc.qcloudimg.com/static/img/e4dbc02ca9ae2a7cb9ada5316effd31a/image.png)
(3) Enter the account (Administrator) and password to log in.

>**Note:**
>This terminal is exclusive, that is, only one user can log in using the console at a time.


**Verify network communications**
Before mounting, you need to confirm the network connectivity between the client and the file system. You can use the telnet command to verify it. The specific protocols and open ports for clients are as follows:

File System Protocol | Open Port for Client | Check Network Connectivity
------- | ------- | ---------
NFS 3.0 | 111, 892, 2049 | telnet 111 or 892 or 2049
NFS 4.0 | 2049 | telnet 2049
CIFS/SMB | 445 | telnet 445 

Note: CFS does not support ping.

## 4. Mounting a File System
### Mount CIFS/SMB file system
#### Mount file system via graphical interface
a. Open **Map Network Drive**
Log in to the Windows, on which you want to mount the file system. Right click **Computer** in the **Start** menu, and then click **Map Network Drive**. 
![](https://mc.qcloudimg.com/static/img/5696d66a83d4e9b35196274f89e07dfc/image.png)
![](https://mc.qcloudimg.com/static/img/6eeb1c0838e6aab185ed8b76dc736912/image.png)

b. Enter the access path
In the pop-up configuration window, set the drive letter and folder (namely, the mounting directory displayed in the CIFS/SMB file system) for the **drive**.
![](https://main.qcloudimg.com/raw/939aafe4bca9907bc391d41e8798c4a6.png)
![](https://mc.qcloudimg.com/static/img/fbfba42f108e2dd0c31599242afa8878/image.png)


c. Verify the correctness of read and write
After confirmation, the page is directed to the mounted file system. You can right click to create a file to verify the correctness of read and write.
![](https://mc.qcloudimg.com/static/img/60b9388885536ec7d81b1cf7f76c39d5/image.png)

#### Mount file system via command line
Use FSID to mount the file system. The mount command is as follows.
```
net use <shared directory name>: \\10.10.11.12\FSID 
```
Example:
```
net use X: \\10.10.11.12\fjie120
```

> **Note:**
> FSID can be found under **Console** -> **File System Details** -> **Mount Point Information**.
![](https://main.qcloudimg.com/raw/939aafe4bca9907bc391d41e8798c4a6.png)


### Mount a NFS file system
#### (1) Enable the NFS service
Before mounting the NFS file system, make sure that the system has enabled the NFS service. Here we use Windows Server 2012 R2 to enable the NFS service.
a. Open **Control Panel** -> **Programs** -> **Turn Windows Features On or Off** -> **Server Roles**, and select **Server for NFS**.
![](https://mc.qcloudimg.com/static/img/eaeed922e9d1f673e47137d80a88fa70/image.png)
b. Open **Control Panel** -> **Programs** -> **Turn Windows Features On or Off** -> **Features**, and select **Client for NFS** to enable the Windows NFS client service.
![](https://mc.qcloudimg.com/static/img/4f9d7ac7b877ceffc5bc2b1d7c050a24/image.png)

#### (2) Verify whether the NFS service is enabled
Open the command line tool under Windows, and execute the following command in the panel. If the relevant NFS information is returned, the NFS client is running normally.
```
mount -h
```
![](https://mc.qcloudimg.com/static/img/4e4f9db217874ccec91ac1f888c8e451/image.png)

#### (3) Add anonymous users and user groups
a. Open the registry
Enter the regedit command in the command line window and press Enter to open the registry window.
![](https://mc.qcloudimg.com/static/img/c9fca9a1b123a5b2dbc69b0ce66d539f/image.png)

b. Add configuration items AnonymousUid and AnonymousGid.
Select the following path in the registry. 
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ClientForNFS\CurrentVersion\Default
```
Right click on the right blank space and the click **Create**. Select **DWORD(32-bit) Value** or **QWORD(64-bit) Value** (depending on the bit count of your OS) in the menu. Then, a new record will appear in the list. Modify the name field to AnonymousUid, and use the default value 0 for the data value. Add another record in the same way, with the name of AnonymousGid and the data value of 0 by default.
![](https://mc.qcloudimg.com/static/img/381cdc3b68fb35be5dcceb2a4c962e33/image.png)
![](https://mc.qcloudimg.com/static/img/80bb0cfbffbed939522459a830df3eac/image.png)

c. Restart the system to make the configuration take effect.
Close the registry and restart the Windows system to complete the registry modification.

##### (4) Mount the file system
###### Mount via graphical interface
a. Open **Map Network Drive**
Log in to the Windows, on which you want to mount the file system. Right click **Computer** in the **Start** menu, and then click **Map Network Drive**. 
![](https://mc.qcloudimg.com/static/img/5696d66a83d4e9b35196274f89e07dfc/image.png)
![](https://mc.qcloudimg.com/static/img/6eeb1c0838e6aab185ed8b76dc736912/image.png)

b. Enter the access path
In the pop-up configuration window, set the drive letter and folder (namely, the mounting directory displayed in the NFS file system) for the **drive**.
![](https://mc.qcloudimg.com/static/img/caa18888e6da73b19de8eefc18ff3680/image.png)
![](https://mc.qcloudimg.com/static/img/fbfba42f108e2dd0c31599242afa8878/image.png)


c. Verify the correctness of read and write
After confirmation, the page is directed to the mounted file system. You can right click to create a file to verify the correctness of read and write.
![](https://mc.qcloudimg.com/static/img/60b9388885536ec7d81b1cf7f76c39d5/image.png)

###### Mount via CMD command line
Enter the following command in the Windows command line tool to mount the file system. The default subdirectory is "nfs".
```
mount  <mount point IP>:/<subdirectory> <shared directory name>:
```
Example:
```
mount 10.10.0.12:/nfs X:
```

If the folder cannot be renamed after the file system is mounted using the above command, use the FSID to mount it. The mount command is as follows.
```
mount <mount point IP>:/FSID <shared directory name>:
```
Example:
```
mount 10.10.0.12:/z3r6k95r X:
```

> **Note:**
> FSID can be found under **Console** -> **File System Details** -> **Mount Point Information**.

![](https://mc.qcloudimg.com/static/img/03550214c0499438e86cfd64b3c377b8/image.png)


### (5) Unmount the file system
#### Unmount a shared directory via graphical interface
To disconnect a mounted file system, right click on the disk and click **Disconnect** from the menu.
![](https://mc.qcloudimg.com/static/img/376cd0547aa64f4d519e5444c5a58f93/image.png)

#### Unmount the NFS shared directory via the CMD command 

When you need to uninstall a shared directory in some cases, use the following command. The "directory name" refers to the full path of the root directory or file system.
```
umount <directory name>:
```
Example:
```
umount X：
```



## 5. Terminating Resources
You can terminate a CVM instance or a file system in the Tencent Cloud console. It is recommended that you terminate any resource that is no longer used, to avoid further fee deduction.
1. Terminate a Tencent Cloud instance. Go to the Tencent Cloud CVM [console](https://console.cloud.tencent.com/cvm/index), and select the instance to be terminated. Click **More** -> **CVM Status**, and then select **Terminate** to terminate the  CVM instance.
![](//mc.qcloudimg.com/static/img/76c588284e3b525702d748b5cd7b8b00/image.png)
2. Terminate a file system. Go to the Tencent Cloud CFS [console](https://console.cloud.tencent.com/cfs), select the file system to be terminated. Click **Delete** and **OK** to delete the file system.
![](//mc.qcloudimg.com/static/img/28cade4807a283ffdcb1fc2a39a7ad88/image.png)



