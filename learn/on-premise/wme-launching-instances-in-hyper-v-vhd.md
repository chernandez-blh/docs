---
title: "Launch Instances in hyper-v using VHD"
id: ""
sidebar_label: "Launch Instances in hyper-v using VHD"
---
---

### Launch instances in hyper-v using VHD
 **Prerequisite**
 - VHD file shared by WaveMaker team 
 - Hyper V with version 10.0.x on Windows 10 Pro
 - Permissions to launch VM 
 
 **Steps**
 
- Open  HYPER V, Right-click on your Hyper-V host, click on New, Select virtual machine for creating a platform virtual machine.
  <br/><br/>
  [![](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/selecting-the-vm-creation-in-hyperv.png)](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/selecting-the-vm-creation-in-hyperv.png)

- Click next on the wizard
  <br/><br/>
  [![](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/click-on-wizard.png)](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/click-on-wizard.png)

- Provide name for the virtual machine and click on next
  <br/><br/>
  [![](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/providing-name.png)](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/providing-name.png)

- Select the generation 1 option click on next
  <br/><br/>
  [![](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/generation-type.png)](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/generation-type.png)

- Enter the memory as 16000 MB. You can use the dynamic memory option as per the requirements and click next
  <br/><br/>
  [![](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/assigning-memory.png)](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/assigning-memory.png)

- Select the switch (Virtual Switch) for the connection and click next
  <br/><br/>
  [![](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/configure-network.png)](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/configure-network.png)
  
- Select Use an existing virtual hard disk option and browse to select the WME platform VM vhd from your local machine. 
  <br/><br/>
  [![](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/virtual-harddisk-connnection.png)](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/virtual-harddisk-connnection.png)

- Verify the summary page and click on finish
  <br/><br/>
  [![](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/verify-the-summary.png)](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/verify-the-summary.png)

- Start and connect to the VM.
  <br/><br/>
  [![](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/start-and-connect-vm.png)](/learn/assets/wme-setup/vm-creation-in-hyperv-using-vhd/start-and-connect-vm.png)

* Also for External Instance or Workspace/AppDeployment Instance launching from Hyper-V  use same procedure