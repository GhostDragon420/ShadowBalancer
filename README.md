# ShadowBalancer: A Brightness Adjuster

🏷️ **BRANDING & ABOUT (SFE LLC)**

* **Product:** ShadowBalancer: A Brightness Adjuster
* **Version:** 1.0.0
* **Status:** SFE LLC Public Release — Free / Open Source
* **Created by:** [Jon Merriman / Juggalospsyco420 / GhostDragon420](https://github.com/GhostDragon420)
* **Copyright:** © 2025–2026 Jon Merriman / Sync-First Essentials LLC
* **Website:** [www.syncfirstessentials.com](https://www.syncfirstessentials.com)
* **Support:** [jon@syncfirstessentials.com](mailto:jon@syncfirstessentials.com)
* **Requires:** 7 Days to Die v3.0, Harmony (ships with the game)

---

## 🧠 Description

7 Days to Die's brightness slider has a bug in v3.0: lowering it below 50% correctly darkens nighttime (indoors and outdoors alike), but it also darkens **indoors during the day** — and it's extreme. Outdoors during the day is unaffected either way.

ShadowBalancer fixes this by replacing the game's single brightness calculation with **four independently configurable values**: indoor/outdoor, day/night. You decide exactly how bright each of the four should be — no more forced darkening indoors just because you turned brightness down for nighttime.

Fully config-driven, with live in-game console commands on top. No recompiling, no DLL edits — just edit the XML or use the console.

---

## ⚠️ Platform & Install Requirements

> [!IMPORTANT]
> **This mod must be installed on the client, not just the server.** Brightness and ambient lighting are calculated locally by each player's own game — this isn't something a server can broadcast or enforce. Installing this only on a server does nothing; each player who wants the fix needs it installed on their own machine.

> [!CAUTION]
> **This mod is not console-compatible.** Consoles (PS5/Xbox) cannot run Harmony (C#) mods under any circumstances — this is a hardware/platform limitation, not a bug, since the fix has to run inside each client's own render loop. PC players get the fix if they install it; console players currently cannot, regardless of server setup.

---

## 📋 Features

* 🌓 **Four Independent Brightness Values** — indoor_day, indoor_night, outdoor_day, outdoor_night, each set separately.
* 📝 **Fully XML-Configurable** — edit `Config/BrightnessOverride.xml` directly, no recompiling.
* 🎮 **Live In-Game Console Commands** — reload, tweak, or reset values without restarting.
* 🛡️ **Range-Validated** — every value is checked against 0.0–2.0 on load and on live edit; out-of-range input is rejected with a clear message instead of silently breaking lighting.
* 🔌 **Zero Vanilla Files Touched** — fully additive via Harmony.

---

## 📦 Installation & Setup

Drop the whole `ShadowBalancer` folder into your Mods folder:

```
7 Days To Die\
└── Mods\
    └── ShadowBalancer\
        ├── ShadowBalancer.dll
        ├── ModInfo.xml
        └── Config\
            └── BrightnessOverride.xml
```

**Requirements:** This mod uses Harmony (`0Harmony.dll`), which 7 Days to Die ships with by default in `Mods\0_TFP_Harmony\`. If that folder already exists in your Mods directory, you're good — nothing extra to install.

After installing, do a **full restart of the game** (not just a world reload). The config file is read once on startup.

There is no installer/uninstaller for this mod — like all standard 7 Days to Die mods, removal is just deleting the `ShadowBalancer` folder from your Mods directory.

---

## ⚙️ Using `Config/BrightnessOverride.xml`

Four values, each between **0.0** (pitch black) and **2.0** (overbright). Anything outside that range is rejected on load and falls back to the default shown below.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<BrightnessOverride>
    <Setting context="indoor_day" value="1.0" />
    <Setting context="indoor_night" value="0.5" />
    <Setting context="outdoor_day" value="1.0" />
    <Setting context="outdoor_night" value="0.5" />
</BrightnessOverride>
```

| Attribute | What it controls |
| :--- | :--- |
| `context` | Which lighting scenario the value applies to: `indoor_day`, `indoor_night`, `outdoor_day`, or `outdoor_night` |
| `value` | The brightness multiplier for that scenario (0.0–2.0) |

The shipped default above already fixes the original bug — night still darkens normally, indoors during the day stays at full brightness regardless of your slider.

---

## 🎮 Console Commands

Registers an `sb` command in the in-game console (F1):

| Command | What it does |
| :--- | :--- |
| `sb reload` | Re-reads `Config/BrightnessOverride.xml` from disk and applies it immediately. No restart needed. |
| `sb set <context> <value>` | Live-tweaks one value (e.g. `sb set indoor_day 0.8`). Validates 0.0–2.0 range and writes the change back to XML if accepted. |
| `sb reset` | Reverts all four values to shipped defaults and saves that back to XML. |

Out-of-range input is rejected with a message stating the valid range — the value stays unchanged.

---

## 📁 Files Included

| File | Description |
| :--- | :--- |
| `ShadowBalancer.dll` | Compiled mod binary (Harmony patch) |
| `ModInfo.xml` | Mod metadata (name, version, author) |
| `Config\BrightnessOverride.xml` | User-editable brightness values |
| `README.md` | This file |
| `LICENSE.md` | End-user license terms |
| `SFE-LLC-ICLA-V1-2-PROFESSIONAL.md` | Contributor License Agreement |

---

## 🔎 How to Tell It's Working

Check the game log on startup for:

```
[ShadowBalancer] InitMod called - loading config and applying Harmony patches...
[ShadowBalancer] Config loaded and Harmony patches applied successfully.
```

If the config is missing or fails to parse, you'll see a warning like:

```
[ShadowBalancer] BrightnessOverride.xml not found. Using shipped defaults.
```

That's not an error state — the mod still works fine on defaults.

---

## 🤝 Support & Collaboration

* **Official Support:** [syncfirstessentials.com](https://www.syncfirstessentials.com)
* **Bug Reports / Nexus Comments:** leave a comment on the mod page
* **Email:** [jon@syncfirstessentials.com](mailto:jon@syncfirstessentials.com)

---

## 🛡️ Legal

© 2025–2026 Jon Merriman / Sync-First Essentials LLC — All Rights Reserved.
See `LICENSE.md` for end-user terms and `SFE-LLC-ICLA-V1-2-PROFESSIONAL.md` for contributor terms.

🌐 [syncfirstessentials.com](https://syncfirstessentials.com) | ✉️ jon@syncfirstessentials.com

This product is part of **Sync-First Essentials LLC**, where the Sync-First idea becomes real.
