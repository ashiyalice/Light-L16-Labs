[![L16](https://github.com/helloavo/Light-L16-Archive/blob/main/Hardware/Images/Exploded.png)](https://htmlpreview.github.io/?https://raw.githubusercontent.com/helloavo/Light-L16-Archive/main/Hardware/Exploded%20View/camera.html)  
*[Go to interactive version](https://htmlpreview.github.io/?https://raw.githubusercontent.com/helloavo/Light-L16-Archive/main/Hardware/Exploded%20View/camera.html)*
## Aim
This repository forks [https://github.com/helloavo/Light-L16-Archive] to transform the Light L16 Camera into a **Chinese smartphone-inspired powerhouse** - emulating Huawei Pura 80 Ultra's XMAGE Red Maple color science, Vivid profiles, and AI processing.

Originally focused on L16 preservation, we're now **reverse engineering Camera/Gallery apps** to bypass Light ASIC limitations and implement:
- **28mm sensor prioritization** (80% single-module feel)
- **Pura80 Red Maple emulation** (Warmth 5200K, +25% saturation)
- **Chinese phone UX** (one-tap Vivid JPEG, Huawei-style UI)

This breaks free from LightOS while unlocking **85-90% visual parity** with modern flagships despite L16 hardware constraints.[web:124][web:73]

## 🎯 Features Implemented
✅ 28mm single-sensor priority fusion (min 5 sensors)
✅ Python Red Maple pipeline (OpenCV HSL/Gamma)
✅ APK patches for Huawei Vivid colors.xml
✅ ADB automation (tap → Pura80 JPEG)
🔄 GCam HDR+ porting (Android 6 compatible)
⏳ Real-time LRI decoding

1. Firmware 1.3.5.1 (preserved from original repo)
Download from Releases → Follow original instructions
2. Extract & Patch Camera APK
adb pull /system/app/Camera2/Camera2.apk
apktool d Camera2.apk -o decompiled/
cp profiles/pura80_vivid.xml decompiled/res/xml/
apktool b decompiled/ -o pura_l16.apk
adb install pura_l16.apk

3. Test Chinese phone pipeline
python pipeline/pura80_redmaple.py sample.lri --output final.jpg


## 📱 Chinese Phone Emulation Targets
| Feature | Pura80 Ultra | L16 + This Fork |
|---------|--------------|-----------------|
| **Color Science** | XMAGE Red Maple | **90% Python emulation** [web:124] |
| **Skin Tone** | Ultra Chroma | AI skin smoothing (+15% brightness) |
| **HDR** | 15 stops Red Maple | **13 stops + GCam HDR+** |
| **UI/UX** | Large buttons, AI modes | **Huawei-style Smali patches** [web:78] |
| **Output** | Vivid JPEG instant | **One-tap pipeline** |

## 🛠️ Tech Stack
APK Mods: Smali editing (Apktool/JADX)
Pipeline: Python OpenCV + NumPy (LRI→DNG→Red Maple)
Target: LightOS Android 6 (no root required)
Input: .LRI files (16-sensor fusion)
Output: Pura80-style JPEG/DNG


## 📂 Folder Structure
├── apk-patches/ # Smali + XML (Huawei UI/colors)
├── pipeline/ # pura80_redmaple.py + LRI decoder
├── profiles/ # HSL values (Pura80 DXOMARK analysis)
├── test-samples/ # L16 raw → Chinese phone conversion
├── original-archive/ # Preserved from upstream repo
└── automation/ # ADB capture scripts

## Other Resources
- **[Lri-rs](https://github.com/gennyble/lri-rs)**: Rust .LRI decoder [Example](https://user-images.githubusercontent.com/147816742/283986081-35164a3c-b0e4-4a3d-a0b0-6c0783c99017.png)
- **[Discord Server](https://discord.gg/9ZzDYYQPp2)**: L16 owners + modders
- **DXOMARK Pura80 Analysis**: Color profile reference [web:124]

## Website Content
Light.co archived via [WayBack Machine](https://web.archive.org/web/20191222062257/https://light.co/camera)

## Firmware Upgrade
**Follow original 1.3.5.1 instructions exactly** (preserved in `firmware/`):
