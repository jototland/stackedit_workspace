
Try this before running apt:

```
$ sudo bash
# mkdir /etc/gcrypt
# echo all >> /etc/gcrypt/hwf.deny

```

Because apt use sha256 method from libgcrypto20, but optimized too much. We can deny this opt. using configuration file  `/etc/gcrypt/hwf.deny`.

EXPLANATION and Solution: Quick Fix

This issue is caused by the Windows Hypervisor Platform. This issue cannot be resolved for now (asfar as I know).

A partial fix is at hand though. And I say"partial" because it involves disabling the platform (also known as"Hyper-V") which will probably break other virtualization solutions you have installed since this is enabled manually. Anyway, here's how to disable it and get your VM running again,

1.  Shut down the Virtual Machine.
    
2.  Press Windows logo key + X, then hit A to run Command Prompt(powershell) as administrator.
    
3.  Type bcdedit /set hypervisorlaunchtype off
    

4.When you see"The operation completed succesfully", reboot your windows. After reboot, boot your VM and update/upgrade.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI2NDQ5ODk1Ml19
-->