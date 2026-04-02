<div align="center">

<br>

```
                                            ________  ___       ________  _________  _______      
                                           |\   ____\|\  \     |\   __  \|\___   ___\\  ___ \     
                                           \ \  \___|\ \  \    \ \  \|\  \|___ \  \_\ \   __/|    
                                            \ \_____  \ \  \    \ \   __  \   \ \  \ \ \  \_|/__  
                                             \|____|\  \ \  \____\ \  \ \  \   \ \  \ \ \  \_|\ \ 
                                               ____\_\  \ \_______\ \__\ \__\   \ \__\ \ \_______\
                                              |\_________\|_______|\|__|\|__|    \|__|  \|_______|
                                              \|_________|                                        
```

<br>

![Windows 11](https://img.shields.io/badge/Windows%2011-222222?style=for-the-badge&logo=windows11&logoColor=white)
![License](https://img.shields.io/badge/License-Apache%202.0-222222?style=for-the-badge)
![Stars](https://img.shields.io/github/stars/dhruvin-sarkar?style=for-the-badge&color=222222)

<br>

</div>

---

> A lightweight Windows 11 setup centred around WezTerm, GlazeWM, and Zebar.

---

## 📺 Showcase

<div align="center">

[![Showcase](https://img.shields.io/badge/YouTube-Watch%20Showcase-222222?style=for-the-badge&logo=youtube&logoColor=white)](https://youtube.com)


</div>

---

## Screenshots

<div align="center">

| Desktop | Terminal | Bar |
|:---:|:---:|:---:|
| `screenshot here` | `screenshot here` | `screenshot here` |

</div>

---

## Stack

| Category | Tool |
|---|---|
| **Terminal** | [WezTerm](https://wezfurlong.org/wezterm/) |
| **Font** | [Custom Iosevka Build](https://github.com/be5invis/Iosevka) |
| **Tiling WM** | [GlazeWM](https://github.com/glzr-io/glazewm) |
| **Status Bar** | [Zebar](https://github.com/glzr-io/zebar) *(vanilla-clear widget)* |
| **App Launcher** | [PowerToys Run](https://github.com/microsoft/PowerToys) |
| **Translucent Taskbar** | [TranslucentTB](https://github.com/TranslucentTB/TranslucentTB) |
| **Wallpaper** | see [Wallpaper](#️-wallpaper) |

---

## Font

This setup uses a **custom-built Iosevka** — not a standard download. Iosevka lets you define your own character shapes, spacing, and ligatures through a build plan before compiling the font yourself.

> [!IMPORTANT]
> Install the font **before** launching WezTerm. WezTerm will fall back silently to a default font if it can't find Iosevka and things will look wrong.

The build plan used here is included as `private-build-plans.toml` in the repo root.

**To build and install:**

1. Install [Node.js](https://nodejs.org/) and clone the Iosevka repo:
   ```bash
   git clone https://github.com/be5invis/Iosevka
   cd Iosevka
   npm install
   ```
2. Copy `private-build-plans.toml` from this repo into the Iosevka root.
3. Build:
   ```bash
   npm run build -- ttf::IosevkaCustom
   ```
4. Fonts output to `dist/IosevkaCustom/TTF/` — right-click each `.ttf` → **Install for all users**.

> [!TIP]
> Preview what different Iosevka variants look like at [typeof.net/Iosevka](https://typeof.net/Iosevka) before committing to a build.

---

## ⚙️ Installation

> [!NOTE]
> Each section shows: `repo file` → `where to put it on your system`

> [!IMPORTANT]
> Back up any configs you already have before copying. All paths are live config locations — merge manually if you already use these tools.

---

### WezTerm *(Terminal)*

[![Tutorial](https://img.shields.io/badge/YouTube-Tutorial-222222?style=flat-square&logo=youtube)](https://www.youtube.com/results?search_query=wezterm+windows+config+tutorial)

WezTerm is a GPU-accelerated terminal emulator with Lua-based configuration. Unlike most terminals that use JSON or YAML, your entire config is a single `.lua` file — making it very flexible and scriptable. It supports splits, tabs, multiplexing, and sixel image rendering out of the box.

Install via winget:
```powershell
winget install wez.wezterm
```

```
wezterm.lua  →  %USERPROFILE%\.wezterm.lua
```

> [!TIP]
> WezTerm hot-reloads on config save — changes apply instantly without restarting the terminal.

---

### GlazeWM *(Tiling Window Manager)*

[![Tutorial](https://img.shields.io/badge/YouTube-Tutorial-222222?style=flat-square&logo=youtube)](https://www.youtube.com/results?search_query=glazewm+windows+tiling+setup+tutorial)

GlazeWM is a tiling window manager for Windows inspired by i3. It automatically arranges open windows into a non-overlapping grid and lets you navigate, move, and resize everything purely through keyboard shortcuts. New windows slot into the layout automatically — no manual snapping.

Install via winget:
```powershell
winget install glzr-io.glazewm
```

```
config.yaml  →  %USERPROFILE%\.glzr\glazewm\config.yaml
```

To autostart: right-click the GlazeWM tray icon → **Run on system startup**, or place a shortcut to `glazewm.exe` in `shell:startup`.

> [!NOTE]
> GlazeWM ships with Zebar pre-bundled — the installer includes a Zebar checkbox so you can set both up in one go.

> [!WARNING]
> GlazeWM will conflict with other window snapping tools (FancyZones, PowerToys snap, Windows 11 snap layouts). Disable those before running GlazeWM or you'll get layout fights.

---

### Zebar *(Status Bar — vanilla-clear widget)*

[![Tutorial](https://img.shields.io/badge/YouTube-Tutorial-222222?style=flat-square&logo=youtube)](https://www.youtube.com/results?search_query=zebar+glazewm+status+bar+setup+tutorial)

Zebar is a customisable status bar that ships with GlazeWM. Widgets are built with HTML, CSS, and JavaScript — you theme them like a webpage. The `Clear Zebar` folder in this repo contains the `vanilla-clear` widget: a clean, minimal top bar with no heavy styling.

Install: bundled with GlazeWM, or standalone from [github.com/glzr-io/zebar](https://github.com/glzr-io/zebar).

**Setup:**
```powershell
# Copy the widget folder into your Zebar directory
cp -r "./Clear Zebar/" "$env:USERPROFILE\.glzr\zebar\"
```

Then open the **Zebar system tray icon** → disable any active widgets → enable `vanilla-clear`.

> [!NOTE]
> Zebar dropped `.yaml` config support in **v2.2.1**. The `zebar-config.yaml` in this repo is kept as a legacy reference for older installs. On v2.2.1 or newer, use the widget folder method above.

> [!CAUTION]
> If Zebar isn't showing after copying the widget, check that the folder name exactly matches what Zebar expects. Name mismatches silently break it — no error, just no bar.

---

### PowerToys Run *(App Launcher / Search)*

[![Tutorial](https://img.shields.io/badge/YouTube-Tutorial-222222?style=flat-square&logo=youtube)](https://www.youtube.com/results?search_query=powertoys+run+windows+tips+setup)

PowerToys Run is a fast keyboard-driven launcher built into Microsoft's PowerToys suite. Think Spotlight on macOS or Rofi on Linux — press a shortcut, start typing, and instantly launch apps, search files, run calculations, open URLs, convert units, and more. It fills the gap that GlazeWM creates by hiding the Start menu and native taskbar.

Install via winget:
```powershell
winget install Microsoft.PowerToys
```

After installing: **PowerToys Settings → PowerToys Run** to set your activation shortcut and enable plugins.

**Useful plugins to turn on:**

| Plugin | What it does |
|---|---|
| Applications | Launch installed apps |
| File Search | Find files and folders instantly |
| Shell | Run PowerShell/CMD commands directly |
| Calculator | Inline math (`2^10`, `sqrt(144)`) |
| Web Search | Open searches in your browser |
| VS Code Workspaces | Jump straight into a project |
| Unit Converter | `10 miles to km`, `500g to lb` |

> [!TIP]
> Set the activation shortcut to `Alt + Space` — it mirrors what most Linux launchers use and doesn't clash with GlazeWM's default `Alt`-based bindings.

> [!NOTE]
> PowerToys Run is one part of a larger suite. Other useful tools in the same install: **Color Picker** (`Win + Shift + C`), **Keyboard Manager** (remap any key), **Always On Top** (`Win + Ctrl + T`), and **Text Extractor** (OCR anything on screen with `Win + Shift + T`).

---

### TranslucentTB *(Translucent Taskbar)*

[![Tutorial](https://img.shields.io/badge/YouTube-Tutorial-222222?style=flat-square&logo=youtube)](https://www.youtube.com/results?search_query=translucenttb+windows+11+setup+tutorial)

TranslucentTB is a lightweight system tray utility that makes the Windows taskbar fully transparent, blurred, or acrylic. Since GlazeWM takes over window management, the taskbar becomes mostly decorative — TranslucentTB lets it blend into your wallpaper rather than sitting as an ugly solid bar at the bottom.

Install from the **Microsoft Store** (recommended — updates automatically):

[![Microsoft Store](https://img.shields.io/badge/Microsoft%20Store-Get%20TranslucentTB-222222?style=flat-square&logo=microsoftedge)](https://apps.microsoft.com/detail/9PF4KZ2VN4W9)

Or via winget:
```powershell
winget install charlesmilette.translucenttb
```

**Recommended settings for this setup:**

| State | Style |
|---|---|
| Desktop (no windows open) | `Clear` |
| Window open | `Blur` |
| Start menu open | `Opaque` |
| Task View | `Blur` |
| Cortana open | `Opaque` |

> [!TIP]
> TranslucentTB's **Dynamic** mode automatically switches between states based on what's active on screen — enable it in the tray icon context menu for a seamless result without manual toggling.

> [!WARNING]
> On some Windows 11 builds, acrylic blur can cause the taskbar to flicker when GlazeWM switches workspaces. If that happens, switch to `Clear` or `Blur` instead of `Acrylic`.

---

Wallpaper used in this setup: **[link here]**

---

## Repo Structure

```
/
├── Clear Zebar/              # Zebar vanilla-clear widget folder
├── config.yaml               # GlazeWM tiling WM config
├── private-build-plans.toml  # Custom Iosevka font build plan
├── wezterm.lua               # WezTerm terminal config
└── zebar-config.yaml         # Legacy Zebar config (pre-v2.2.1 reference)
```

---

## Notes

> [!CAUTION]
> This config was built for a specific monitor layout. If your bar or tiling looks off, adjust workspace and monitor settings in `config.yaml`.

- **Resolution** — `1920×1080` *(update with yours)*
- **Shell** — PowerShell Core (`pwsh`)

---

## Credits

- [r/unixporn](https://reddit.com/r/unixporn)
- [glzr-io](https://github.com/glzr-io) for GlazeWM + Zebar
- [be5invis](https://github.com/be5invis) for Iosevka
- [TranslucentTB](https://github.com/TranslucentTB/TranslucentTB) contributors
- [Microsoft PowerToys](https://github.com/microsoft/PowerToys) team

---

<div align="center">

<br>

*if this helped, a ⭐ is appreciated*

<br>

</div>
