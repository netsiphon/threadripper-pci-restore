# Threadripper PCI Restore

Restore PCI state on Threadripper x399 platform is no longer required. Please feel free to use the script to compile your kernel and install packages if necessary but due to changes in X399 BIOS for PCI Reset option (BIOS option added at least to Asrock X399 Taichi v3.30) and changes introduced in 4.19 for pci_restore_config_dword with boolean force option, the previous patch should no longer be necessary.

## Ubuntu 18.04 LTS example:
### Download the latest full kernel release version ...example here is 4.19
```
wget https://github.com/torvalds/linux/archive/v4.19.zip
unzip v4.19.zip
```
### Clone this repo
```
git clone https://github.com/netsiphon/threadripper-pci-restore.git
cd threadripper-pci-restore/
```
### Replace configuration with your OS kernel configuration from /boot
_Please note that the make-custom-kernel script is set to generate 32 threads for the 1950x. Choose the appropriate number for an alternate model._
```
./make-custom-kernel ../linux-4.19 config-4.15.0-38-generic

```
Restart to use the new kernel
