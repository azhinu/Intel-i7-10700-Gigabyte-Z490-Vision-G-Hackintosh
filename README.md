# Intel-i7-10700-Gigabyte-Z490-Vision-G-Hackintosh



Tested working version:
 - macOS Catalina 10.15.7

## Bootloader

**[Opencore](https://github.com/acidanthera/OpenCorePkg) 0.6.6**

## Hardware

- Intel i7-10700 (Locked version)
- [Gigabyte Z490 Vision G](https://www.gigabyte.com/Motherboard/Z490-VISION-G-rev-1x):
  - Audio: Realtek ALC1220-V
  - 2.5Gb Ethernet: Intel I225-V
- No dGPU
- BIOS: F8
- SMBIOS: iMac20,1


## Working

- **Audio**: Realtek ALC1220-V (AppleALC.kext, layout-id=7, device-id=0xA170, FakeID.kext, FakePCIID_Intel_HDMI_Audio.kext)

- **USB**: All ports working, USB map is shown below

- **Ethernet**: Intel I225-V 2.5Gb

- **iGPU**: UHD 630. Working two 4K displays (But laggy a bit). No DRM in Safari.

- Native NVRAM

- Sleep/Wake

- Reboot/Shutdown


## USB Ports

See [USB-Port-Configuration.md](./USB-Port-Configuration.md)

## Audio

Needed:

- AppleALC.kext
- FakeID.kext
- FakePCIID_Intel_HDMI_Audio.kext
- layout-id=7
- device-id=0xA170

Layout-id and device-id is injected via the device properties.

```xml
<key>DeviceProperties</key>
	<dict>
		<key>Add</key>
		<dict>
			<key>PciRoot(0x0)/Pci(0x1F,0x3)</key>
			<dict>
				<key>device-id</key>
				<data>cKEAAA==</data>
				<key>layout-id</key>
				<data>BwAAAA==</data>
			</dict>
		</dict>
	</dict>
```


## BIOS Setting

- Disable
  - CSM Support
  - Secure Boot
  - CFG Lock
- Enable
  - VT-x
  - VT-d
  - Above 4G Decoding
  - Hyper-Threading
  - Onboard GPU Memory: 64MB


## Credits

- [Apple](https://www.apple.com) : Awesome macOS
- [Acidanthera](https://github.com/acidanthera) : OpencorePkg, kexts, tools etc.
- [Dortania](https://github.com/dortania) : Opencore guide
- [headkaze](https://github.com/headkaze/Hackintool) : Hackintool
- [samuel21119](https://github.com/samuel21119/Intel-i7-10700-Gigabyte-Z490-Vision-G-Hackintosh) : Base for Configuration
- [augstb](https://github.com/augstb/Hackintosh-Intel-i7-10700k-Gigabyte-Z490-Vision-G) : iGPU reference
