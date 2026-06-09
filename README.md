# Lotus IDE — Board Catalog

Default board catalog for [Lotus IDE](https://github.com/jaturong-kamonlers/LotusIDE-Releases) v1.5.0+.

Open the IDE → **Lotus → Manage Boards → Available** → click **Fetch catalog** to install any of the boards below.

## Boards

| ID | Title | Platform | Description |
|---|---|---|---|
| `LotusDevkit` | LotusDevkit | `arduino-esp32` | ESP32 dev board (OLED + RGB + buzzer + IR remote) |
| `LotusDevkit4Wheels` | LotusDevkit 4 Wheels | `arduino-esp32` | ESP32 4-wheel robot platform |
| `LotusNanoBot` | LotusNanoBOT | `arduino-avr` | Nano AVR robot (L9110S motors + IR + ultrasonic) |
| `LotusMegaBot` | LotusMegaBot | `arduino-avr` | Mega AVR robot (multi-servo + peripherals) |
| `LotusMegaBotPlus` | LotusMegaBot++ | `arduino-avr` | Mega 2560 + TFT + 6 motors + 9 servos |
| `LotusDueBot` | LotusDueBot | `arduino-sam` | Arduino Due (32-bit ARM, TFT, IMU, SD) |

## Why install from catalog when the boards already ship bundled?

User-installed boards (under `<userData>/boards/<id>/`) **override** the bundled copy at `<app>/public/boards/<id>/`. Publishing fixes here lets users update an individual board without waiting for a new IDE release — useful when a `config.js` pin number changes or a header file ships a bug fix.

## Repository layout

```
catalog.json          ← Default catalog the IDE fetches on first open.
icons/<board>.jpg     ← 200xN thumbnail (~10-13 KB) for the Available tab.
<board>.zip           ← Full board package (config.js, block/, static/, include/).
```

## Updating a board

1. Update the source under `LotusIDE/public/boards/<id>/`.
2. Re-zip with `Compress-Archive` (Windows) or `zip -r` (Unix).
3. Replace `<board>.zip` here and bump `version` in `catalog.json`.
4. Commit + push to `main` — installs pick up the new version next time the user clicks **Available → Fetch catalog**.
