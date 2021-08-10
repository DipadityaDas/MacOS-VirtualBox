# MacOS Big Sur in Virtual Box 

## Pre-requisites for the Setup

1. [Oracle Virtual Box](https://www.virtualbox.org/)
2. [Oracle VM VirtualBox Extension Pack](https://www.virtualbox.org/wiki/Downloads)
3. [MacOS Big Sur ISO file](http://www.mediafire.com/file/dbfod9u5q9ii9nd/macOS_Big_Sur_11.0.1_%252820B29%2529.iso/file)

---
## Steps to Install macOS Big Sur on VirtualBox on Windows

- Install VirtualBox on Windows PC
- Install/Update VirtualBox Extension
- Create a New Virtual Machine & Customize it
- Run VirtualBox Code to the Command Prompt
- Start the Virtual Machine
- Perform Clean Installation of macOS Big Sur

---
## Necessary Virtual Box Commands

#### Before executing the following command, make sure to set the environment path for Virtual Box CLI Tools

- Change the CPU configuration of Virtual Box
```shell
VBoxManage.exe modifyvm "VM Name" --cpuid-set 00000001 000106e5 00100800 0098e3fd bfebfbff
```

- Change the System Product
```shell
VBoxManage setextradata "VM Name" VBoxInternal/Devices/efi/0/Config/DmiSystemProduct "MacBookPro16,1"
```

- Change the Product Signature
```shell
VBoxManage setextradata "MacOS" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Mac-E1008331FDC96864"
```

- Change the Device Key
```shell
VBoxManage setextradata "MacOS" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"
```

- Change the value of smc or else the VM will go to Panic attack.
```shell
VBoxManage setextradata "MacOS" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1
```

- Change the Resolution of the MacOS VM accordingly 
```shell
VBoxManage setextradata "MacOS" VBoxInternal2/EfiGraphicsResolution 1920x1080
```

- After the Installation of the MacOS, we can remove the verbose to some extend.
```shell
VBoxManage setextradata "MacOS" VBoxInternal2/EfiBootArgs "usb=0x800 keepsyms=1 -serial=0x1"
```