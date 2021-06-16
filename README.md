# Hackintosh-Intel-i5-10400-Gigabyte-Z490M-Gaming-X
# Hardware:

CPU: [Intel Core 10 Gen i5-10400]

Motherboard: [GIGABYTE Z490M Gaming X]

GPU: [RX 570 4GB]

Wifi/Bluetooth: [fenvi HB-FV1200]
# Bootloader:

Opencore 0.7.0

# Installation Steps:

**Most of these steps comes from the [dortania's](https://dortania.github.io/OpenCore-Desktop-Guide/) installation guide.** Make sure to read those instructions.

## config.plist

- Download OpenCorePkg's releases.

- Rename the sample.plist file in "Docs" under the OpenCorePkg folder

- Copy the file to "EFI/OC" on the usb

- Download ProperTree and start the program

  [corpnewt/ProperTree](https://github.com/corpnewt/ProperTree)

- Open your config.plist in the app

- And change all configurations mentioned in

  [Comet Lake](https://dortania.github.io/OpenCore-Desktop-Guide/config.plist/comet-lake.html#pciroot0x0pci0x20x0)

- Use CorpNewt's GenSMBIOS application to generate SMBIOS info, and add it to config.plist.

Disabled: SetupVirtualMap may be needed depending on the firmware, generally this quirk should be avoided but most Gigabyte users and older hardware(Broadwell and older) will need this quirk to boot.

Added SSDT-AWAC.aml to config.plist

## Bios Settings

**Disable:**

- Fast Boot
- VT-d (can be enabled if you set `DisableIoMapper` to YES)
- CSM
- Thunderbolt(For initial install, as Thunderbolt can cause issues if not setup correctly)
- Intel SGX
- Intel Platform Trust
- CFG Lock (MSR 0xE2 write protection) (**This must be off, if you can't find the option then enable both `AppleCpuPmCfgLock` and `AppleXcpmCfgLock` under Kernel -> Quirks. Your hack will not boot with CFG-Lock enabled**) **NOT FOUND**

**Enable:**

- VT-x
- Above 4G decoding
- Hyper-Threading
- Execute Disable Bit
- EHCI/XHCI Hand-off
- OS type: (Windows 10 Feautres: Ohter)
- DVMT Pre-Allocated(iGPU Memory): 64MB

# Post Installation

1. Boot without USB: Copy the EFI folder on the usb to the mounted efi on main computer using "Mount EFI".

   [corpnewt/MountEFI](https://github.com/corpnewt/MountEFI)

2. Exclude Verbose Mode
