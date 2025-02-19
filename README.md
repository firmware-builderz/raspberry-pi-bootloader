# Raspberry Pi Boot-Dateien

Diese README beschreibt die notwendigen Dateien, um verschiedene Raspberry Pi Modelle zu booten. Jede Version des Raspberry Pi benötigt spezifische Dateien, um erfolgreich zu starten.

## Raspberry Pi 1 (Model A, B, B+)
- `bootcode.bin`
- `start.elf`
- `fixup.dat`
- `kernel.img`
- `cmdline.txt`
- `config.txt`

## Raspberry Pi 2 (Model B)
- `bootcode.bin`
- `start.elf`
- `fixup.dat`
- `kernel7.img`
- `cmdline.txt`
- `config.txt`

## Raspberry Pi 3 (Model A+, B, B+)
- `bootcode.bin`
- `start.elf`
- `fixup.dat`
- `kernel7.img`
- `cmdline.txt`
- `config.txt`
- `bcm2710-rpi-3-b.dtb` (Device Tree Blob)
- `bcm2710-rpi-3-b-plus.dtb` (Für Model 3B+)

## Raspberry Pi 4 (Model B, Compute Module 4)
- `start4.elf`
- `fixup4.dat`
- `kernel7l.img`
- `cmdline.txt`
- `config.txt`
- `bcm2711-rpi-4-b.dtb` (Device Tree Blob)
- `bootcode.bin` (optional, für ältere Firmware)

## Raspberry Pi 5
- `start4.elf`
- `fixup4.dat`
- `kernel8.img`
- `cmdline.txt`
- `config.txt`
- `bcm2712-rpi-5.dtb` (Device Tree Blob)

## Allgemeine Hinweise
- `cmdline.txt`: Enthält Kernel-Bootparameter.
- `config.txt`: Konfigurationsdatei für Boot-Optionen.
- `*.dtb`: Device Tree Blob für die jeweilige Hardware.
- `kernel*.img`: Kernel-Datei für das entsprechende Modell (z. B. `kernel7.img` für Raspberry Pi 2 & 3, `kernel8.img` für Raspberry Pi 5).

Alle Dateien müssen auf einer FAT32-formatierten Boot-Partition gespeichert werden, damit der Raspberry Pi sie lesen kann.

Hier sind die `config.txt` und `cmdline.txt` Dateien für das Raspberry Pi 1 bis 5.  

### **config.txt für alle Modelle**  
Jedes Raspberry Pi Modell hat unterschiedliche Hardwareanforderungen, daher werden die Konfigurationsdateien entsprechend angepasst.

#### **Raspberry Pi 1 (Model A/B, A+/B+, Zero, Zero W)**
```ini
# config.txt für Raspberry Pi 1
arm_freq=700
gpu_mem=16
dtoverlay=disable-bt
dtoverlay=disable-wifi
```

#### **Raspberry Pi 2 (alle Versionen)**
```ini
# config.txt für Raspberry Pi 2
arm_freq=900
gpu_mem=32
dtoverlay=disable-bt
dtoverlay=disable-wifi
```

#### **Raspberry Pi 3 (Model B, B+, Zero 2 W)**
```ini
# config.txt für Raspberry Pi 3
arm_freq=1200
gpu_mem=64
dtoverlay=disable-bt
dtoverlay=disable-wifi
enable_uart=1
```

#### **Raspberry Pi 4 (alle Versionen)**
```ini
# config.txt für Raspberry Pi 4
arm_freq=1500
gpu_mem=128
dtoverlay=vc4-fkms-v3d
max_framebuffers=2
enable_uart=1
arm_64bit=1
```

#### **Raspberry Pi 5**
```ini
# config.txt für Raspberry Pi 5
arm_freq=2400
gpu_mem=128
dtoverlay=vc4-kms-v3d
max_framebuffers=2
enable_uart=1
arm_64bit=1
```

---

### **cmdline.txt für alle Modelle**  
Die `cmdline.txt` enthält Kernel-Parameter und ist für alle Modelle weitgehend gleich.

```txt
console=serial0,115200 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 rootwait quiet
```
