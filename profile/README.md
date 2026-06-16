<div align="center">

# 🏠 Home Ops

### Open-source building blocks for a local-first smart home

Practical, self-hosted home automation built on
**[Home Assistant](https://www.home-assistant.io/)** + **[ESPHome](https://esphome.io/)** —
HVAC control, ESP32 devices, add-ons, and tooling. **No cloud required.**

<br>

![Home Assistant](https://img.shields.io/badge/Home%20Assistant-41BDF5?style=for-the-badge&logo=home-assistant&logoColor=white)
![ESPHome](https://img.shields.io/badge/ESPHome-000000?style=for-the-badge&logo=esphome&logoColor=white)
![ESP32](https://img.shields.io/badge/ESP32-E7352C?style=for-the-badge&logo=espressif&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)

</div>

---

We build small, focused, **vendor-neutral** components that make hardware talk to Home
Assistant over local protocols — RS-485, BLE, IR — and the tooling to ship and
operate them. Everything here runs on your own network and is wired to HA through the
native API, HACS, or the add-on store.

<br>

## 🎬 Spotlight — an open Logitech Harmony replacement

Harmony is dead. HomeOps is rebuilding the universal-remote experience from local,
open building blocks — no cloud, no discontinued hub:

- **📡 IR for legacy gear** — [`esphome-ir-codegen`](https://github.com/HomeOps/esphome-ir-codegen)
  generates ESPHome IR packages straight from the [Flipper-IRDB](https://github.com/Lucaslhm/Flipper-IRDB):
  TVs, AV receivers, soundbars, and anything with an IR window.
- **🔵 BLE for modern devices** — [`esphome-blekeyboard`](https://github.com/HomeOps/esphome-blekeyboard)
  drives Android TV, streaming sticks, and PCs as a native Bluetooth keyboard.
- **🎚️ Activities** — *coming soon:* a Home Assistant integration that ties these into
  Harmony-style **Activities** ("Watch TV", "Play Movie") — one tap sets every device,
  input, and volume.

<br>

## 🌡️ Climate &amp; HVAC

Reverse-engineered, fully local control for Midea-style heat pumps and any climate device.

| Project | What it does | |
|---|---|---|
| **[ESPHome-Midea-XYE](https://github.com/HomeOps/ESPHome-Midea-XYE)** | ESPHome external component that drives Midea HVAC over the **XYE / CCM RS-485 bus** — a native HA climate entity with full mode, fan, and setpoint support. Includes [protocol docs](https://github.com/HomeOps/ESPHome-Midea-XYE/blob/main/esphome/components/midea_xye/PROTOCOL.md). | ![stars](https://img.shields.io/github/stars/HomeOps/ESPHome-Midea-XYE?style=flat&label=%E2%98%85&color=f5c518) |
| **[py-ccm15](https://github.com/HomeOps/py-ccm15)** | Async Python library for the **Midea CCM-15** central controller — bridges the RS-485 VRF bus to TCP/IP and controls up to 64 indoor units over HTTP. `pip install py-ccm15`. | ![stars](https://img.shields.io/github/stars/HomeOps/py-ccm15?style=flat&label=%E2%98%85&color=f5c518) |
| **[HASS-Smart-Climate](https://github.com/HomeOps/HASS-Smart-Climate)** | HACS integration that turns **any** climate device into an EcoBee-like smart thermostat — **areas with their own sensors per preset** (each preset follows the rooms that matter at that time), comfort presets, automatic heat/cool switching, and short-cycle protection. | ![stars](https://img.shields.io/github/stars/HomeOps/HASS-Smart-Climate?style=flat&label=%E2%98%85&color=f5c518) |

<br>

## 📟 ESP32 Devices &amp; ESPHome

Firmware and codegen for inexpensive ESP32 hardware that integrates over the native HA API.

| Project | What it does | |
|---|---|---|
| **[esphome-hass-panels](https://github.com/HomeOps/esphome-hass-panels)** | ESPHome firmware for a **Guition ESP32-S3 touchscreen** — swipe-navigable LVGL pages for an `alarm_control_panel` keypad and a `climate` thermostat, with PIN entry and state animations. | ![stars](https://img.shields.io/github/stars/HomeOps/esphome-hass-panels?style=flat&label=%E2%98%85&color=f5c518) |
| **[esphome-blekeyboard](https://github.com/HomeOps/esphome-blekeyboard)** | ESPHome component that turns an ESP32 into a **BLE HID keyboard** — recognized natively by Windows, Android, and iOS, with secure pairing and key-combo support. CI-gated with pinnable `release-please` tags. | ![stars](https://img.shields.io/github/stars/HomeOps/esphome-blekeyboard?style=flat&label=%E2%98%85&color=f5c518) |

<br>

## 📦 Add-ons

Services that install straight from the Home Assistant add-on store.

| Project | What it does | |
|---|---|---|
| **[esphome-ir-codegen](https://github.com/HomeOps/esphome-ir-codegen)** | **The Logitech Harmony is dead — build your own.** A HA add-on that auto-generates ESPHome `remote_transmitter` packages from the open **[Flipper-IRDB](https://github.com/Lucaslhm/Flipper-IRDB)** (and HA `infrared-protocols`), so a ~$20 ESP32 becomes a Home-Assistant-driven universal remote. IR codes are pulled live at compile time — never hand-typed. | ![stars](https://img.shields.io/github/stars/HomeOps/esphome-ir-codegen?style=flat&label=%E2%98%85&color=f5c518) |

<br>

## 🧩 Tooling

| Project | What it does | |
|---|---|---|
| **[PwrHass](https://github.com/HomeOps/PwrHass)** | PowerShell client for Home Assistant — call services and query entity state from the shell after a one-time `Connect-HomeAssistant`. On the PowerShell Gallery. | ![stars](https://img.shields.io/github/stars/HomeOps/PwrHass?style=flat&label=%E2%98%85&color=f5c518) |

<br>

## 🛠️ How it fits together

```text
        ┌─────────────────────── Home Assistant ───────────────────────┐
        │   native API  ·  HACS integrations  ·  add-on store  ·  REST  │
        └────────┬────────────────┬───────────────┬──────────────┬─────┘
                 │                │               │              │
            XYE RS-485        CCM-15 / IP      LVGL panel       IR / BLE
                 │                │               │              │
          ESPHome-Midea       py-ccm15      esphome-hass    esphome-blekeyboard
             -XYE           HASS-Smart        -panels       esphome-ir-codegen*
                            -Climate                        (*add-on)
```

<br>

## 🤝 Contributing

Most repos use **Conventional Commits** + **release-please** for automated versioning,
and CI compile gates for the ESPHome components. Issues, PRs, and protocol findings are
welcome — open one on the relevant repo. Everything here is built to run on your own
hardware, on your own network.

<div align="center">
<br>

*Local-first. Vendor-neutral. Yours to own.*

</div>
