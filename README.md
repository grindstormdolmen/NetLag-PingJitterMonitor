<p align="center">
  <img src="https://i.postimg.cc/3RbPC79s/banner.png" alt="NetLag Network HUD — Live Ping, Jitter & Packet Loss Overlay for Online Gaming" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-Live%20Ping%20%26%20Jitter%20HUD-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-netlag--hud--v1.2-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

# NetLag Network HUD — Live Ping, Jitter & Packet Loss Overlay for Online Gaming

**Experiencing sudden rubberbanding in Valorant, CS2, Warzone, Apex, or Helldivers 2 and unsure whether it's your home Wi-Fi router, ISP bufferbloat, or the game server? Pin a tiny click-through Ping, Jitter, and Packet Loss pill on screen to see exact network stability live.**

NetLag Network HUD runs lightweight ICMP/UDP latency probes to both your **local router gateway (`192.168.1.1`)** and **internet backbone endpoints (`1.1.1.1` / `8.8.8.8` / regional game endpoints)**: **instantly showing whether lag spikes come from your local Wi-Fi or your ISP**.

This project is aimed at **Windows 10 and Windows 11 (64-bit) online gamers** troubleshooting Wi-Fi interference, router bufferbloat, and packet loss in Borderless Windowed games.

## Quick Use-Case & Troubleshooting Reference

| Scenario / Issue | Cause | Solution |
| --- | --- | --- |
| Sudden rubberbanding even though in-game ping shows '30 ms' | High **Jitter** (`15–60 ms` variance) or `2%–5%` **Packet Loss** between ticks | Monitor rolling **Jitter (ms)** and **Packet Loss %** over the last 100 probes |
| Unsure if lag is caused by home Wi-Fi or ISP/game server | In-game netgraphs don't separate local router hop from internet hop | Probe **Router Gateway (`192.168.x.x`)** alongside **Internet (`1.1.1.1`)** simultaneously |
| Heavy overlay suites eat CPU or inject into anti-cheat games | In-process overlays conflict with Vanguard, EAC, or BattlEye | Render an external click-through `WS_EX_TRANSPARENT` pill with zero DLL hooks |
| Need to hide the ping bar when recording or watching videos | Permanent desktop widgets stay visible on screenshots | Toggle visibility anytime with global hotkey `Ctrl+Alt+P` |

## Download for Windows

[**Download NetLagHUD.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/NetLagHUD.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why use `NetLagHUD.exe`? (Key features)

- Displays live **Ping (ms)**, **Jitter (ms)**, **Packet Loss %**, and a compact color-coded latency sparkline.
- Dual-hop diagnostics: compares **Local Router Ping** vs. **External Internet Ping** so you immediately know if Wi-Fi is spiking.
- Pure external click-through overlay (`< 12 MB` RAM)—zero game process injection and 100% anti-cheat safe.
- Toggle on/off anytime with `Ctrl+Alt+P` and export a CSV log if contacting your ISP about packet loss.

### Sample Output

```text
[NetLagHUD] Network Telemetry Active (Hotkey: Ctrl+Alt+P | Probe Interval: 250ms)
[OK]   Internet (1.1.1.1) : Ping: 21 ms | Jitter: 1.8 ms | Packet Loss: 0.0%
[OK]   Router (192.168.1.1): Ping:  1 ms | Jitter: 0.4 ms | Wi-Fi Signal: Strong (96%)
```

The release ZIP is named `NetLagHUD.zip`; the Windows executable inside is named `NetLagHUD.exe`.

1. Close NetLag HUD before updating or replacing executable files.
2. Click **Download NetLagHUD.zip** above.
3. Right-click the downloaded archive and choose **Extract All**.
4. Open the extracted folder and run `NetLagHUD.exe`.
5. Review the options and output paths before processing files.

**Requirements:** Windows 10 or 11 (64-bit) with an active internet connection.

### Verification & Windows SmartScreen Note

- **Offline & standard user permissions:** `NetLagHUD.exe` runs locally without uploading your personal files and does not require disabling Windows Defender.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Problems this project solves

### Pinpointing Wi-Fi router spikes vs. ISP packet loss

If Router ping jumps from `1 ms` to `85 ms`, your Wi-Fi or local download is the culprit; if Router stays `1 ms` while Internet spikes, the issue is your ISP or server.

### Exposing hidden jitter that causes missed shots

Shows millisecond variance (`Jitter`) that average ping counters hide.

### Zero anti-cheat interference

Runs as a standard external layered overlay window without touching game binaries.

### Exportable CSV connection log for ISP support tickets

Log timestamped packet loss events to prove line instability to your provider.

## Default folders and configuration paths

NetLag HUD stores layout preferences and optional CSV logs in `%APPDATA%\NetLagHUD`:

```text
%APPDATA%\NetLagHUD\config.json
```

Typical directory layout:

```text
NetLag Overlay Pill (Click-Through Topmost):
[ PING 21ms | JIT 1.8ms | LOSS 0.0% | LAN 1ms ]
```

Run games in **Borderless Windowed** mode so external overlays render cleanly above the game frame.

## Quick start guide

Follow these steps to get started:

1. **Extract `NetLagHUD.zip` and launch `NetLagHUD.exe`.** Your default router gateway and primary probe target are detected automatically.
2. **Drag the compact HUD pill to your preferred screen corner and lock position.** Launch your game in Borderless Windowed mode.
3. **Press `Ctrl+Alt+P` anytime to show or hide the overlay.** Optionally enable **Log Spikes to CSV** when diagnosing ISP packet loss.

### Data safety note

NetLag HUD sends low-bandwidth standard ping probes (~250 bytes/sec) with negligible bandwidth impact.

## What the status summary shows

NetLag HUD displays **internet ping ms, jitter ms, packet loss %, local router ping ms, and toggle hotkey**.

## FAQ

**Is NetLag HUD safe to use in games with Vanguard, EAC, or BattlEye?**

Yes—it is a pure external click-through overlay window and does not inject code into or read memory from any game.

**How do I tell if my lag is from Wi-Fi or my ISP?**

Watch the `LAN` (router) number next to `PING`: if `LAN` spikes above `15–20 ms`, something on your home Wi-Fi/network is causing lag; if `LAN` stays `1–2 ms` while `PING` spikes, the delay is outside your home router.

**Does running NetLag HUD use noticeable bandwidth?**

No—at 4 probes per second, it uses less than 1 KB/s (under 0.01 Mbps).

## Useful reading

- [Waveform Bufferbloat & Latency Test Reference](https://www.waveform.com/tools/bufferbloat)

## More Windows Gaming Utilities

- [MiniHUD-LightweightFPSOverlay](../MiniHUD-LightweightFPSOverlay) — Compact borderless FPS, frametime & GPU temp overlay
- [NetPing-DNSGameSwitcher](../NetPing-DNSGameSwitcher) — Game server ping tester, Winsock reset & DNS switcher
- [PortWatch-LocalPortKiller](../PortWatch-LocalPortKiller) — Find & free blocked Windows TCP/UDP ports in one click
- [CrosshairDot-CustomGamingOverlay](../CrosshairDot-CustomGamingOverlay) — Click-through custom screen crosshair & PNG reticle overlay

*Independent open-source desktop utility for Windows.*
