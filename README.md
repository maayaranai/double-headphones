# Double Headphones

[![Support on Ko-fi](https://img.shields.io/badge/Ko--fi-Support%20Development-ff5e5b?logo=ko-fi&logoColor=white)](https://ko-fi.com/doubleheadphones)

**Share audio to multiple headphones simultaneously on Windows. No drivers, no complexity.**

**Free forever -- donations appreciated.**

Two people, one laptop, two headphones. Watch movies together, each with your own pair.

[Download the latest release](https://github.com/double-headphones/double-headphones/releases)

---

![Screenshot placeholder](docs/screenshot.png)

---

## How It Works

Double Headphones captures audio from a specific application (like Chrome or VLC), then sends that same audio to two or more output devices at the same time. It uses built-in Windows audio APIs -- no virtual audio drivers, no kernel modifications, no complicated routing.

1. You pick the app that is playing audio (e.g., your browser).
2. You pick two headphones (or any two audio outputs).
3. You press Share. Both headphones play the same audio in sync.

When you stop sharing, everything goes back to normal automatically.

## Features

- **Multi-device output** -- play audio on two or more devices simultaneously
- **Per-app capture** -- capture audio from a single application, not the entire system
- **No drivers required** -- pure user-mode Windows APIs, nothing to install at the system level
- **Simple interface** -- three dropdowns and one button, nothing more
- **Bluetooth support** -- works with Bluetooth headphones, wired headphones, USB DACs, speakers, or any mix
- **Independent volume control** -- adjust volume for each output device separately
- **Latency compensation** -- adjustable delay slider to sync Bluetooth audio with video
- **Clock drift correction** -- automatic sample-rate drift compensation for long listening sessions
- **Crash recovery** -- if the app exits unexpectedly, your system audio is restored to its original state
- **System tray mode** -- minimize to tray and forget about it
- **Lightweight** -- under 50 MB installed, under 5% CPU usage
- **Free forever** -- no ads, no telemetry, no trial limits

## System Requirements

| Requirement | Minimum |
|-------------|---------|
| Operating System | Windows 10 build 20348 or later, or Windows 11 |
| Architecture | 64-bit (x64) |
| Runtime | .NET 8 (included in the installer) |
| Audio | At least two audio output devices connected |
| RAM | 50 MB |
| Disk | 50 MB |

> **Why build 20348?** Double Headphones uses the Process Loopback Capture API introduced in that build. Earlier versions of Windows 10 do not have this API. You can check your build number by pressing Win+R, typing `winver`, and pressing Enter.

## Installation

### Option A: Installer (recommended)

1. Download `DoubleHeadphones-1.0.0-Setup.exe` from the [Releases](https://github.com/double-headphones/double-headphones/releases) page.
2. Run the installer. It will guide you through setup.
3. Optionally create a desktop shortcut and enable "start with Windows."
4. Launch Double Headphones from the Start Menu or desktop shortcut.

### Option B: Portable

1. Download `DoubleHeadphones-1.0.0-portable.zip` from the [Releases](https://github.com/double-headphones/double-headphones/releases) page.
2. Extract to any folder.
3. Run `DoubleHeadphones.exe`.

No administrator privileges are required for either option.

## Usage

1. **Connect your headphones.** Pair or plug in both audio devices. Make sure Windows recognizes them (check Sound Settings).
2. **Start playing media.** Open your browser, media player, or any app and start playing audio or video.
3. **Open Double Headphones.** Launch the application.
4. **Select the audio source.** In the "Audio Source" dropdown, pick the app that is playing audio (e.g., "Chrome", "VLC").
5. **Select Device A.** Choose the first headphone or output device.
6. **Select Device B.** Choose the second headphone or output device.
7. **Click Share.** Both devices will start playing the same audio.
8. **Adjust volume.** Use the per-device volume sliders if one pair is louder than the other.
9. **Adjust latency (if needed).** If Bluetooth audio is slightly behind the video, use the latency slider to add a delay to the wired device so they match.
10. **Click Stop** when you are done. The app restores your original audio routing.

## FAQ

### Why can I still hear faint audio from my laptop speakers?

Double Headphones lowers the source app's volume to near-zero (-40 dB) on the original output to keep the audio pipeline alive. This is effectively inaudible in most environments. It does not fully mute because Windows may suspend the audio pipeline for muted apps, which would break the capture.

### Netflix / Disney+ audio is silent when sharing

Streaming apps that use DRM (Digital Rights Management) with Protected Media Path will block audio capture. This is a Windows-level protection that no user-mode application can bypass.

**Workaround:** Use a web browser (Chrome is recommended) instead of the native Windows app. Browser-played audio is not protected by the same mechanism.

### Audio is out of sync with video

Bluetooth headphones introduce 150-250ms of latency due to the Bluetooth A2DP encoding and transmission process. This is a physics limitation of the Bluetooth protocol, not a bug.

**Fix:** Use the latency compensation slider in Double Headphones to add a matching delay to the non-Bluetooth device. Most video players also have their own audio delay settings -- check your player's preferences.

### Can I use more than 2 devices?

The architecture supports N output devices. Version 1.0 ships with a two-device interface. Multi-device support (3+) is planned for a future release.

### Does it work with gaming audio?

Yes, as long as the game uses standard Windows audio (WASAPI Shared Mode). Games using ASIO or WASAPI Exclusive Mode cannot be captured.

### Does it work with Spotify / system sounds?

Yes. Any application that appears in the Windows Volume Mixer can be captured.

## Known Limitations

These are honest constraints that cannot be solved at the application level:

- **DRM-protected content** -- Apps using Protected Media Path (Netflix Windows app, Edge with PlayReady) will produce silence. Use Chrome as a workaround.
- **Bluetooth latency** -- Bluetooth A2DP adds 150-250ms of inherent delay. The latency slider helps, but cannot eliminate it.
- **Dual Bluetooth on a single adapter** -- Running two Bluetooth headphones on one Bluetooth radio may cause audio dropouts depending on adapter firmware. A second USB Bluetooth adapter is recommended if you experience issues.
- **ASIO applications** -- Apps using ASIO bypass Windows audio entirely and cannot be captured.
- **Exclusive mode applications** -- Apps that lock an audio device in WASAPI Exclusive Mode cannot be captured.
- **Windows 10 builds before 20348** -- The Process Loopback API does not exist on older builds. The app requires build 20348+.
- **Elevated processes** -- If the source app is running as Administrator and Double Headphones is not, capture may fail. Run Double Headphones as Administrator in that case.

## Tech Stack

| Component | Technology |
|-----------|------------|
| Language | C# 12 |
| Framework | .NET 8, WPF |
| Audio API | WASAPI (via NAudio) |
| Win32 Interop | CsWin32 source generator |
| System Tray | H.NotifyIcon.Wpf |
| Installer | Inno Setup |
| Target | Windows 10/11, x64 |

## Building from Source

```bash
git clone https://github.com/double-headphones/double-headphones.git
cd double-headphones
dotnet publish src/DoubleHeadphones/DoubleHeadphones.csproj -c Release -o publish
```

To build the installer, install [Inno Setup 6](https://jrsoftware.org/isinfo.php) and compile `installer/setup.iss`.

## Contributing

Contributions are welcome. Please:

1. Fork the repository and create a feature branch.
2. Follow the existing code style (C# conventions, nullable enabled).
3. Test on both Windows 10 (build 20348+) and Windows 11 if possible.
4. Open a pull request with a clear description of the change.

For bug reports, please include your Windows version (`winver`), audio device types, and the app you were trying to capture.

## Support

If Double Headphones is useful to you, consider [buying me a coffee on Ko-fi](https://ko-fi.com/doubleheadphones). It helps fund continued development and new features.

## License

Proprietary -- free for personal use. See [LICENSE](LICENSE) for the full text.

## Credits

- [NAudio](https://github.com/naudio/NAudio) -- .NET audio library by Mark Heath
- [H.NotifyIcon](https://github.com/HavenDV/H.NotifyIcon) -- WPF system tray icon library
- [CsWin32](https://github.com/microsoft/CsWin32) -- Win32 P/Invoke source generator by Microsoft
- [Inno Setup](https://jrsoftware.org/isinfo.php) -- Installer compiler by Jordan Russell
