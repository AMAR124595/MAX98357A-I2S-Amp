# MAX98357A I2S Class-D Audio Amplifier 

Custom 2-layer PCB design for a compact **mono I2S digital audio amplifier** based on the **MAX98357AETE+T**.

This board provides a complete digital-to-speaker solution with an integrated DAC and filterless Class-D output stage, intended for embedded and production-oriented audio systems.

---

## Overview

The MAX98357A integrates:

* Digital I2S audio interface
* Internal DAC
* High-efficiency Class-D amplifier
* Automatic clock detection

This PCB is designed for direct integration with:

* ESP32
* STM32
* Raspberry Pi
* Any MCU supporting I2S output

---

## Main IC

**Part Number:** MAX98357AETE+T
**Package:** TQFN-16 (3mm × 3mm, 0.5mm pitch, exposed pad)
**Manufacturer:** Analog Devices / Maxim Integrated

### Key Characteristics

* Supply range: 2.7V – 5.5V
* Output power: up to 3.2W into 4Ω @ 5V
* Sample rate: 8kHz – 96kHz
* Differential BTL output
* > 90% typical efficiency

---

## Technical Specifications

| Parameter             | Value              |
| --------------------- | ------------------ |
| Supply Voltage        | 2.7V – 5.5V        |
| Recommended Operation | 5V                 |
| Output Power          | 3.2W @ 4Ω          |
| Output Type           | Differential (BTL) |
| Audio Interface       | I2S                |
| PCB Layers            | 2-Layer            |

---

## Interface

### I2S Input Header (J2 – 1x7, 2.54mm)

| Pin   | Function    |
| ----- | ----------- |
| VIN   | 5V Supply   |
| GND   | Ground      |
| BCLK  | Bit Clock   |
| LRCLK | Word Select |
| DIN   | Serial Data |
| SD    | Shutdown    |
| GAIN  | Gain Select |

### Speaker Output (J1 – 3.5mm Terminal Block)

* OUTP
* OUTN

⚠️ Speaker must be connected between OUTP and OUTN.
Do not connect either output to ground.

---

## Bill of Materials

| Reference | Value                 | Footprint                | Qty |
| --------- | --------------------- | ------------------------ | --- |
| U1        | MAX98357A             | TQFN-16-1EP_3x3mm_P0.5mm | 1   |
| C1        | 22pF                  | 0603                     | 1   |
| C2        | 10µF                  | 0603                     | 1   |
| C3        | 0.1µF                 | 0402                     | 1   |
| C4, C5    | 220pF                 | 0402                     | 2   |
| FB1, FB2  | 100Ω @100MHz, 3A      | 0603                     | 2   |
| R1        | 1MΩ                   | 0603                     | 1   |
| J1        | Terminal Block 3.5mm  | —                        | 1   |
| J2        | 1x7 Pin Header 2.54mm | —                        | 1   |
| TP1       | OUTN Test Pad         | 1mm Pad                  | 1   |
| TP2       | OUTP Test Pad         | 1mm Pad                  | 1   |

Full fabrication files are available in the repository.

---

## PCB Design Notes

### Power & Decoupling

* 10µF bulk capacitor near VIN entry
* 0.1µF placed close to VDD
* Solid ground plane implemented
* Exposed pad tied to GND with multiple vias

### Signal Integrity

* Short I2S routing
* Differential outputs routed symmetrically
* Wide copper traces for speaker current

### EMI Control

* Ferrite beads on both output lines
* 220pF capacitors for high-frequency suppression
* Minimized switching loop area

---

## Validation Procedure

1. Apply 5V supply without speaker → verify idle current.
2. Probe BCLK, LRCLK, and DIN using oscilloscope.
3. Connect 4Ω speaker and inject test tone.
4. Verify clean differential waveform.
5. Monitor IC temperature at high output levels.

---

## Repository Contents

* Documentation
* Schematic files
* PCB layout files
* BOM

---

## Manufacturing Notes

* Reflow soldering recommended for TQFN package.
* Proper stencil aperture for exposed pad.
* Ensure adequate thermal grounding.
* Ferrite beads must support ≥3A peak current.
* Avoid thermal relief on exposed pad.

---

## Applications

* Embedded audio systems
* Smart speakers
* IoT voice modules
* Portable digital audio devices
* Industrial alert systems

---

## References

* [https://www.analog.com/media/en/technical-documentation/data-sheets/MAX98357A-MAX98357B.pdf](https://www.analog.com/media/en/technical-documentation/data-sheets/MAX98357A-MAX98357B.pdf)
* [https://www.analog.com/media/en/technical-documentation/data-sheets/MAX98357DEVTQFN-MAX98357EVSYSTQFN.pdf](https://www.analog.com/media/en/technical-documentation/data-sheets/MAX98357DEVTQFN-MAX98357EVSYSTQFN.pdf)
* [https://www.adafruit.com/product/3006](https://www.adafruit.com/product/3006)
* [https://robu.in/wp-content/uploads/2021/10/MAX98357AETET.pdf](https://robu.in/wp-content/uploads/2021/10/MAX98357AETET.pdf)

---

## Author

**Amar Gangadhar**
Electronics Engineer | Embedded Systems Designer |  Embedded Firmware Developer | PCB Design Engineer

---
