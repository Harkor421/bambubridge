# BambuBridge

BambuBridge sends your Bambu Lab printers' cameras to the [BambuFarm](https://bambufarm.app) app, so you can watch them from anywhere.

Your printers' cameras only work on your local network. BambuBridge runs on a computer (or a small ESP32 board) on that network and relays the video to BambuFarm. You don't need port forwarding or a VPN. A camera only streams while someone is watching it.

**Download:** [bambufarm.app/#bridge](https://bambufarm.app/#bridge) · [All releases](https://github.com/Harkor421/bambubridge/releases)

| Platform | File |
|---|---|
| macOS 13+ (Apple silicon) | `BambuBridge-<version>-mac-arm64.dmg` |
| macOS 13+ (Intel) | `BambuBridge-<version>-mac-x64.dmg` |
| macOS 12 Monterey | `BambuBridge-<version>-mac-legacy-x64.dmg` (Intel) / `mac-legacy-arm64.dmg` (Apple silicon) |
| Windows 10/11 | `BambuBridge-<version>-windows-setup.exe` |
| Linux x64 | `.AppImage` or `.deb` (`linux-x86_64` / `linux-amd64`) |
| Linux ARM64 (Raspberry Pi 4/5, etc.) | `.AppImage` or `.deb` (`linux-arm64`) |
| ESP32 (beta) | `esp32s3-factory.bin` / `esp32-factory.bin` |

## Getting started

1. Install BambuBridge on a computer that stays on and is on the same network as your printers.
2. Sign in with your Bambu Lab account, the same one you use in BambuFarm.
3. BambuBridge finds your printers. Open a camera in BambuFarm and it goes live.

**Windows:** if SmartScreen says "Windows protected your PC", click **More info → Run anyway**.

**macOS:** when macOS asks to let BambuBridge find devices on your local network, click **Allow**.

**X1, H2 and P2S:** on the printer, turn on **LAN Mode Liveview** (Settings → Network).

## ESP32 (beta)

The ESP32 version streams the cameras of P1P, P1S, A1 and A1 mini printers without a computer. It needs a board with PSRAM, such as an ESP32-S3 N8R8 or N16R8 (2 cameras at once) or an ESP32-WROVER (1 camera).

Flash the factory image at offset `0x0`, for example with [ESP Web Flasher](https://espressif.github.io/esptool-js/) or:

```sh
esptool.py --chip esp32s3 write_flash 0x0 BambuBridge-<version>-esp32s3-factory.bin
```

When the board powers up it creates a Wi-Fi network called **BambuBridge-XXXX**. Join it from your phone to set it up. Hold **BOOT** for 5 seconds to reset it.

## Support

Join the [BambuFarm Discord](https://discord.gg/9ug2PVPfRh).
