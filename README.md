# Threadripper PCI Restore
Restore PCI state on Threadripper x399 platform

Patch from https://patchwork.kernel.org/patch/10181903/ which has yet to be included in mainline linux kernel.

## Ubuntu 16.04 LTS example:
### Download the latest full kernel release version ...example here is 4.17
```
wget https://github.com/torvalds/linux/archive/v4.17.zip
unzip v4.17.zip
```
### Clone this repo and patch
```
git clone https://github.com/netsiphon/threadripper-pci-restore.git
cd threadripper-pci-restore/
patch -d ../linux-4.17 -p0 < threadripper-kernel-pci-restore.patch 
```
All hunks must succeed to proceed. If they don't look for the failed hunk and manually correct it if you can.

### Replace configuration with your OS kernel configuration from /boot
_Please note that the make-custom-kernel script is set to generate 32 threads for the 1950x. Choose the appropriate number for an alternate model._
```
./make-custom-kernel ../linux-4.17 config-4.4.0-128-generic
```
Restart to use the new kernel (as long as you don't see any PCI related errors).
