---
title: "Launch Instances in GCP"
id: ""
sidebar_label: "Launch Instances in GCP"
---
---

### Launch instances in GCP
**Prerequisite**
- Having access in GCP to create instances and other resources.for more details visit [IAM and permissions in GCP](https://cloud.google.com/compute/docs/access/iam)
- Assuming VPC is already created .for creating VPC in GCP visit [VPC creation in GCP](https://cloud.google.com/vpc/docs/using-vpc)

**Steps**  

**Firewall Rules for Platform and External Instance**
- For creating firewall rules and more details visit [firewall rules in GCP](https://cloud.google.com/vpc/docs/using-firewalls)
- For WME setup in GCP require 3 firewall rules ,are
  - wme-sg-platform-public 
  - wme-sg-platform-internal
  - wme-sg-workspace-internal
- **Create firewall rules for public access to the platform instance**
  - Provide basic details name and network details for firewall.
	   <br/><br/>
     [![](/learn/assets/wme-setup/wme-setup-in-gcp/platform-public-firewall-name-and-network.png)](/learn/assets/wme-setup/wme-setup-in-gcp/platform-public-firewall-name-and-network.png)
  - Select target type and source filter type.by using the target we can connect the firewall rule to instance.example the which instance have target tag the firewall is connect to that instance and by using the source we can open ports to specific instance.example the which instance have a source tag the rules will be open to that instance.we provide this tags at network section during the instance creation.
   <br/><br/>
   [![](/learn/assets/wme-setup/wme-setup-in-gcp/platform-public-firewall-targets-and-ports.png)](/learn/assets/wme-setup/wme-setup-in-gcp/platform-public-firewall-targets-and-ports.png)

- **Create a firewall rule for platform instance for access from the external instance**
  - Provide basic details name and network details for firewall
	   <br/><br/>
     [![](/learn/assets/wme-setup/wme-setup-in-gcp/platform-internal-firewall-name-and-network.png)](/learn/assets/wme-setup/platform-internal-firewall-name-and-network.png)
  - Select target type and source filter type.by using the target we can connect the firewall rule to instance.example the which instance have target tag the firewall is connect to that instance and by using the source we can open ports to specific instance.example the which instance have a source tag the rules will be open to that instance.we provide this tags at network section during the instance creation.
   <br/><br/>
   [![](/learn/assets/wme-setup/wme-setup-in-gcp/platform-internal-firewall-target-and-ports.png)](/learn/assets/wme-setup/wme-setup-in-gcp/platform-internal-firewall-target-and-ports.png)

- **Create firewall rule for external instance for access from the platform instance**
  - Provide basic details name and network details for firewall
	   <br/><br/>
     [![](/learn/assets/wme-setup/wme-setup-in-gcp/external-instance-firewall-name-and-network.png)](/learn/assets/wme-setup/external-instance-firewall-name-and-network.png)
   - Select target type and source filter type.by using the target we can connect the firewall rule to instance.example the which instance have target tag the firewall is connect to that instance and by using the source we can open ports to specific instance.example the which instance have a source tag the rules will be open to that instance.we provide this tags at network section during the instance creation.
   <br/><br/>
   [![](/learn/assets/wme-setup/wme-setup-in-gcp/external-instance-firewall-target-and-ports.png)](/learn/assets/wme-setup/wme-setup-in-gcp/external-instance-firewall-target-and-ports.png)
   <br/><br/>

**Creating a Platform Instance**

- Select region,zone and provide name for instance.select machine type with minimum 16 GB memory
	  <br/><br/>
    [![](/learn/assets/wme-setup/wme-setup-in-gcp/platform-instance-region-and-zone.png)](/learn/assets/wme-setup/platform-instance-region-and-zone.png)

- Select image or snapshot for creating boot disk.select operating system as ubuntu and version as ubuntu 16.04 LTS 
    <br/><br/>
    [![](/learn/assets/wme-setup/wme-setup-in-gcp/instance-boot-disk.png)](/learn/assets/wme-setup/instance-boot-disk.png)

- Provide ssh key details in security for accessing the instance 
    <br/><br/>
    [![](/learn/assets/wme-setup/wme-setup-in-gcp/instance-ssh-security.png)](/learn/assets/wme-setup/instance-ssh-security.png)

- At disk section create disks for wm-data and wm-runtime with 150 and 50 GiB
	  <br/><br/>
    [![](/learn/assets/wme-setup/wme-setup-in-gcp/platform-instance-disk.png)](/learn/assets/wme-setup/wme-setup-in-gcp/platform-instance-disk.png)

- At network section provide respected network tags of your firewall if you using source and target tags at firewall rules and create instance.
	  <br/><br/>
    [![](/learn/assets/wme-setup/wme-setup-in-gcp/platform-instance-networking.jpg)](/learn/assets/wme-setup/wme-setup-in-gcp/platform-instance-networking.jpg)
    <br/><br/>

**Creating a External Instance**
- Select region,zone and provide name for instance.select machine type.
    <br/><br/>
    [![](/learn/assets/wme-setup/wme-setup-in-gcp/external-region-and-zone.png)](/learn/assets/wme-setup/wme-setup-in-gcp/external-region-and-zone.png)

- Select image or snapshot for creating boot disk.select operating system as ubuntu and version as ubuntu 16.04 LTS 
    <br/><br/>
    [![](/learn/assets/wme-setup/wme-setup-in-gcp/instance-boot-disk.png)](/learn/assets/wme-setup/instance-boot-disk.png)

- Provide ssh key details in security for accessing the instance 
    <br/><br/>
    [![](/learn/assets/wme-setup/wme-setup-in-gcp/instance-ssh-security.png)](/learn/assets/wme-setup/instance-ssh-security.png)

- At disk section create disk for external instance usage with minimum of 100 GiB
	  <br/><br/>
    [![](/learn/assets/wme-setup/wme-setup-in-gcp/external-instance-disk.png)](/learn/assets/wme-setup/wme-setup-in-gcp/external-instance-disk.png)

- At network section provide respected network tags of your firewall if you using source and target tags at firewall rules and create instance.
	  <br/><br/>
    [![](/learn/assets/wme-setup/wme-setup-in-gcp/external-instance-network.jpg)](/learn/assets/wme-setup/wme-setup-in-gcp/external-instance-network.jpg)
    <br/><br/>

**Mounting Disks in Platform Instance**
- For ssh into the platform instance use the following command.
     - For login use the following command
     ```
     ssh -i /path/to/ssh-privatekey username@ipaddress
     ```
  -  Check your list of block devices available by using the following command
         ```
           lsblk
           ```
  -  New volumes are raw block devices, and you must create a file system on them before you can mount and use them. For creating file systems use following command
     -  mkfs -t ext4 /dev/< block-device-name >
      ```
       Example: mkfs -t ext4 /dev/sdc
       ```
  -  Use the mkdir command to create a mount point directory for the volume. The mount point is where the volume is located in the file system tree and where you read and write files to after you mount the volume.for wme-setup create two directories.create directories using the following commands
      ```
       mkdir /wm-data /wm-runtime
      ```
  -  Use the following command to mount the volume at the directory
      ```
       mount /dev/block-device-name    /directory  
      ```
      [![](/learn/assets/wme-setup/wme-setup-in-gcp/mounting-volumes-platform.png)](/learn/assets/wme-setup/wme-setup-in-gcp/mounting-volumes-platform.png)


  - To mount an attached Disk on every system reboot, add an entry for the device to the /etc/fstab file.
      - Take UUID of disks for identification by using the command
          ```
          blkid
          ```
      - Entry the UUID of the disks in fstab.use the following format
     ```
    UUID=your-block-device-UUID      mount-directory     filesystem     defaults ,nofail  0  2
     ```
  	  <br/><br/>
      [![](/learn/assets/wme-setup/wme-setup-in-gcp/fstab-platform.png)](/learn/assets/wme-setup/wme-setup-in-gcp/fstab-platform.png)

**Mounting Disks in External or Workspace/AppDeployment Instance**
- For ssh into the platform virtual machine use the following command.
   - For login use the following command
   ```
   ssh -i /path/to/ssh-privatekey username@ipaddress
   ```
-  Check your list of block devices available by using the following command
       ```
         lsblk
         ```
-  New volumes are raw block devices, and you must create a file system on them before you can mount and use them. For creating file systems use following command
   -  mkfs -t ext4 /dev/< block-device-name >
    ```
     Example: mkfs -t ext4 /dev/sdc
     ```
-  Use the mkdir command to create a mount point directory for the volume. The mount point is where the volume is located in the file system tree and where you read and write files to after you mount the volume.for wme-setup create two directories.create directories using the following commands
    ```
     mkdir /data
    ```
-  Use the following command to mount the volume at the directory
    ```
     mount /dev/block-device-name    /directory  
    ```
    [![](/learn/assets/wme-setup/wme-setup-in-gcp/external-instance-volume-mounting.png)](/learn/assets/wme-setup/wme-setup-in-gcp/external-instance-volume-mounting.png)

- To mount an attached Disk on every system reboot, add an entry for the device to the /etc/fstab file.
    - Take UUID of disks for identification by using the command
        ```
        blkid
        ```
    - Entry the UUID of the disks in fstab.use the following format
   ```
  UUID=your-block-device-UUID      mount-directory     filesystem     defaults ,nofail  0  2
   ```
	  <br/><br/>
    [![](/learn/assets/wme-setup/wme-setup-in-gcp/fstab-platform.png)](/learn/assets/wme-setup/wme-setup-in-gcp/external-instance-fstab.png)
  
