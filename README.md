# Music Studio Setup Documentation

A comprehensive guide for setting up and operating a hybrid hardware/software music production studio centered around a Mac Studio and Universal Audio Apollo interface.

## Table of Contents
- [Overview](#overview)
- [System Diagram](#system-diagram)
- [Connection Guide](#connection-guide)
  - [USB Connections](#usb-connections)
  - [MIDI Cables](#midi-cables)
  - [Audio Cables](#audio-cables)
- [Power Requirements](#power-requirements)
- [Setup Instructions](#setup-instructions)
- [Workflow Guide](#workflow-guide)

## Overview

This studio setup combines modern digital audio workstation capabilities with analog synthesis and effects processing. The system is built around a Mac Studio as the central hub, utilizing a Universal Audio Apollo Twin X for professional audio conversion and the ESI M4U eX for extensive MIDI routing capabilities.

## System Diagram

```mermaid
graph TB
    %% Computer and Interface
    MAC[Mac Studio]
    APOLLO[UA Apollo Twin X]
    MIDI_HUB[ESI M4U eX<br/>MIDI Interface]

    %% MIDI Controllers
    KEY37[Arturia KeyStep 37]
    PADK[KORG PadKontrol]

    %% Sound Sources
    MICRO[Arturia MicroFreak]
    VOLCAFM[Korg Volca FM2]
    NUBASS[Korg Volca Nubass]
    DM12[Behringer Deepmind 12D]
    PROMINI[Behringer Pro VS Mini]
    STREICH[Waldorf Streichfett]
    TR6S[Roland TR6s]
    BB[1010 Music Blackbox]

    %% Effects
    WALRUS[Walrus Audio Fundamental]
    NTS3[Korg NTS-3]

    %% Mixer
    MIXER[Behringer RX1602 V2<br/>Rackmount Mixer]

    %% USB Connections
    MAC -->|USB-C| APOLLO
    MAC -->|USB| MIDI_HUB

    %% MIDI Controllers to Interface
    KEY37 -->|USB| MIDI_HUB
    PADK -->|USB| MIDI_HUB

    %% MIDI Connections
    MIDI_HUB -->|MIDI| MICRO
    MIDI_HUB -->|MIDI| VOLCAFM
    MIDI_HUB -->|MIDI| NUBASS
    MIDI_HUB -->|MIDI| DM12
    MIDI_HUB -->|MIDI| PROMINI
    MIDI_HUB -->|MIDI| STREICH
    MIDI_HUB -->|MIDI| TR6S
    MIDI_HUB -->|MIDI| BB

    %% Audio Connections to Mixer
    MICRO -->|Audio| MIXER
    VOLCAFM -->|Audio| MIXER
    NUBASS -->|Audio| MIXER
    DM12 -->|Audio| MIXER
    STREICH -->|Audio| MIXER
    TR6S -->|Audio| MIXER

    %% Effects Loop
    MIXER -->|MON/FX Send| WALRUS
    WALRUS -->|Return to Ch.8| MIXER

    %% Main Output Path
    MIXER -->|Main Out| NTS3
    NTS3 -->|Audio| APOLLO
    APOLLO -->|Audio| MAC

    %% Control Room Path
    APOLLO -->|Control Room Out| BB
    BB -->|Audio| APOLLO

    classDef computer fill:#f9f,stroke:#333,stroke-width:2px
    classDef interface fill:#ff9,stroke:#333,stroke-width:2px
    classDef controller fill:#9ff,stroke:#333,stroke-width:2px
    classDef synth fill:#9f9,stroke:#333,stroke-width:2px
    classDef effect fill:#f99,stroke:#333,stroke-width:2px
    classDef mixer fill:#999,stroke:#333,stroke-width:2px

    class MAC computer
    class APOLLO,MIDI_HUB interface
    class KEY37,PADK controller
    class MICRO,VOLCAFM,NUBASS,DM12,PROMINI,STREICH,TR6S,BB synth
    class WALRUS,NTS3 effect
    class MIXER mixer
```

## Connection Guide

### USB Connections
| Device | Cable Type | Quantity | Notes |
|--------|------------|----------|--------|
| UA Apollo Twin X | USB-C to USB-C | 1 | Thunderbolt connection preferred |
| ESI M4U eX | USB-B to USB-A | 1 | USB 3.0 recommended |
| Arturia KeyStep 37 | USB-B to USB-A | 1 | Also provides power |
| KORG PadKontrol | USB-B to USB-A | 1 | Also provides power |
| 1010 Music Blackbox | USB-C to USB-A | 1 | For file transfer and updates |

### MIDI Cables
| Connection | Cable Type | Quantity | Notes |
|------------|------------|----------|--------|
| ESI M4U eX to MicroFreak | 5-pin DIN MIDI | 1 | |
| ESI M4U eX to Volca FM2 | 5-pin DIN to 3.5mm MIDI | 1 | Requires MIDI adapter |
| ESI M4U eX to Volca Nubass | 5-pin DIN to 3.5mm MIDI | 1 | Requires MIDI adapter |
| ESI M4U eX to Deepmind 12D | 5-pin DIN MIDI | 1 | |
| ESI M4U eX to Pro VS Mini | 5-pin DIN MIDI | 1 | |
| ESI M4U eX to Streichfett | 5-pin DIN MIDI | 1 | |
| ESI M4U eX to TR6s | 5-pin DIN MIDI | 1 | |

### Audio Cables
| Connection | Cable Type | Quantity | Notes |
|------------|------------|----------|--------|
| Synths to RX1602 (Ch.1-7) | 1/4" TRS or 3.5mm to 1/4" | 14 | Stereo pairs for each input |
| RX1602 MON/FX Send to Walrus | 1/4" TRS | 2 | Stereo effects send |
| Walrus to RX1602 (Ch.8) | 1/4" TRS | 2 | Effects return to last channel |
| RX1602 Main Out to NTS-3 | 1/4" TRS | 2 | Stereo pair |
| NTS-3 to Apollo Twin | 1/4" TRS | 2 | Stereo pair |
| Apollo Control Room to Blackbox | 1/4" TRS | 2 | Stereo pair |
| Blackbox to Apollo Twin | 1/4" TRS | 2 | Stereo pair |

## Power Requirements
| Device | Power Type | Notes |
|--------|------------|--------|
| UA Apollo Twin X | External PSU | Included PSU required |
| ESI M4U eX | USB Powered | No additional PSU needed |
| Arturia KeyStep 37 | USB Powered | No additional PSU needed |
| KORG PadKontrol | USB Powered | No additional PSU needed |
| Arturia MicroFreak | 12V DC | PSU included |
| Korg Volca FM2 | 9V DC or 6x AA | Power supply recommended |
| Korg Volca Nubass | 9V DC or 6x AA | Power supply recommended |
| Behringer Deepmind 12D | IEC Power Cable | Standard computer power cable |
| Behringer Pro VS Mini | 12V DC | PSU included |
| Waldorf Streichfett | 12V DC | PSU included |
| Roland TR6s | USB-C or 9V DC | Can use USB power |
| 1010 Music Blackbox | USB-C | Power via USB-C |
| Behringer RX1602 V2 | IEC Power Cable | Standard computer power cable |
| Walrus Fundamental | 9V DC | Standard pedal power |
| Korg NTS-3 | USB-C or Battery | USB power recommended |

## Setup Instructions

1. **Computer Setup**
   - Install Universal Audio Console software
   - Configure MIDI devices in DAW preferences
   - Set audio interface buffer size based on needs
   - Configure Apollo Control Room routing

2. **Hardware Connection Order**
   - Connect and power on Apollo Twin X first
   - Connect MIDI interface and controllers
   - Power on synthesizers and effects
   - Configure MIDI channels on each device

3. **Signal Flow Configuration**
   - Set input gains on RX1602 mixer for each stereo channel
   - Connect Walrus Fundamental to MON/FX send and channel 8
   - Set MON level to zero on all channels initially
   - Configure Apollo Control Room output level
   - Test MIDI routing through ESI interface
   - Verify audio paths through all outputs

## Workflow Guide

1. **Recording Setup**
   - Route desired synths to stereo mixer channels 1-7
   - Set appropriate gain staging per stereo pair
   - Use channel 8 to blend in Walrus effects
   - Configure Apollo Control Room for Blackbox monitoring
   - Arm DAW tracks for recording

2. **MIDI Control**
   - KeyStep 37 for melodic input
   - PadKontrol for drum programming
   - Configure MIDI channels per instrument
   - Use DAW for MIDI sequencing

3. **Audio Processing**
   - Use MON knobs to send signals to Walrus effects
   - Blend effects return on channel 8 with dry signals
   - Use NTS-3 on main output for master effects
   - Use Apollo Control Room for Blackbox sampling
   - Apply Apollo Twin effects for final processing

4. **Effects Management**
   - Adjust individual MON sends per channel for effects depth
   - Use channel 8 fader to control overall effects level
   - Pan channel 8 to taste for stereo effects placement
   - Monitor effects mix through main outputs
   - Use Apollo Console for Control Room routing
