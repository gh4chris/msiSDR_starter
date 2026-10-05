## Design Background

The **SDR RSP1 Simple** is a low-cost Software Defined Radio (SDR) receiver based on the **MSi001** tuner and **MSi2500** ADC/USB interface from Mirics. It originated from the open-source MSI.SDR project, which was developed as a hardware implementation inspired by the architecture of the SDRplay RSP1.

### Mirics Architecture Overview

The SDR RSP1 Simple is built around two highly integrated Mirics devices. The MSi001 provides RF tuning, filtering, amplification, and quadrature signal generation, while the MSi2500 performs high-speed analog-to-digital conversion and USB data transport.

For detailed technical information, refer to the official Mirics datasheets:
- [MSi001 Datasheet R3P3](https://github.com/gh4chris/msiSDR_starter/blob/master/docs/datasheets/MSi001%20Datasheet%20R3P3.pdf)
- [MSi2500 Datasheet R1P1](https://github.com/gh4chris/msiSDR_starter/blob/master/docs/datasheets/MSi2500%20Datasheet%20R1P1.pdf)

Additional background information about the Mirics chipset family and the relationship between the MSi001 and MSi002 tuner variants can be found in the following overview document:

- [MSi001 / MSi002 Product Overview](https://github.com/gh4chris/msiSDR_starter/blob/master/docs/datasheets/MSi001-MSi002.pdf)

#### MSi001 Multi-Band Tuner Architecture

![MSi001 Block Diagram](https://raw.githubusercontent.com/gh4chris/msiSDR_starter/master/docs/schematics/msi001-BlockDiagram.jpg)

#### MSi2500 ADC and USB Interface Architecture

![MSi2500 Block Diagram](https://raw.githubusercontent.com/gh4chris/msiSDR_starter/master/docs/schematics/msi2500-BlockDiagram.jpg)

### Stringed together ###
![SDR System Block](https://raw.githubusercontent.com/gh4chris/msiSDR_starter/master/docs/schematics/2021-11-22_08h13_48-1024x768.jpg)

The following diagrams illustrates how the tuner, ADC, and host interface interact within a typical SDR receiver architecture:

![SDR System Block Diagram](https://raw.githubusercontent.com/gh4chris/msiSDR_starter/master/docs/schematics/rsp2-diagram.jpg)


The original design was created within the maker community of **Huanghuai University** and published on the Chinese technology forum **Kechuang** as an open-source project. The goal was to provide a high-performance yet affordable SDR platform using the Mirics chipset. The original project discussion and design documentation are available in the [Kechuang project thread](https://www.kechuang.org/t/83757).

According to the EasyEDA project title block, the schematic and PCB layout were created by **Frank.May**. The design itself is commonly associated with the amateur radio callsign **BG7YZF**, under which several enhanced versions and small production runs were offered.

Building on the original open-source work, later revisions introduced several practical improvements while fully utilizing the capabilities of the MSi001/MSi2500 architecture.

➡️ [Vendor Images and Later Board Revisions](https://github.com/gh4chris/msiSDR_starter/blob/master/docs/vendorimg/readme.md) gallery.

The revisions attributed to BG7YZF include:

- Redesigned PCB layout
- USB Type-C interface
- Additional band-pass filtering from 60 MHz to 1000 MHz
- Optimized RF grounding and layout techniques
- Additional stitching vias to improve RF performance

The result is the **SDR RSP1 Simple**, a compact wideband SDR receiver featuring five band-filtered antenna inputs and a USB-C interface. While the circuit was intentionally simplified to reduce manufacturing cost, it retains the core functionality of the original design and continues to leverage the proven combination of the **MSi001** tuner and **MSi2500** digital processing chipset.

## Technical Overview

The later board revisions are available in two variants: **Simple** and **Full**. All designs are based on the same MSi001 and MSi2500 chipset combination and provide the same core SDR functionality. The differences are primarily related to cost, usability, frequency stability, and RF front-end implementation.

The SDR RSP1 Simple offers:

- Frequency coverage from approximately **10 kHz to 1 GHz**
- A small coverage gap between **250 MHz and 400 MHz**
- Up to **10 MHz instantaneous bandwidth**
- Approximately **60 dB signal-to-noise ratio (SNR)**

The effective ADC resolution depends on the selected sample rate:

| Sample Rate | Effective Resolution |
|-------------|----------------------|
| 2–6 MSPS | 14 Bit |
| 6–8 MSPS | 12 Bit |
| 8–9 MSPS | 10 Bit |
| 9–10 MSPS | 8 Bit |

### Simple vs. Full Version

Two hardware variants were offered by BG7YZF:

#### SDR RSP1 Simple

The Simple version was designed as a low-cost implementation and features:

- Manual antenna selection
- Standard active crystal oscillator
- Simplified RF filtering
- No enclosure
- Reduced component count
- Frequency coverage up to approximately 1 GHz

#### SDR RSP1 Full

The Full version includes several enhancements:

- 0.5 ppm TCXO for improved frequency accuracy
- Enhanced RF filtering
- Improved receiver sensitivity
- Better selectivity
- Easier operation due to the integrated antenna switching circuitry
- Improved overall RF performance

### Design Philosophy

The differences between the two versions are mainly the result of cost-reduction decisions rather than fundamental architectural changes. Both receivers use the same MSi001 tuner and MSi2500 ADC/USB interface and therefore provide the same basic feature set.

According to information provided by BG7YZF, most improvements implemented in the Full version can also be retrofitted to the Simple version by experienced users. These modifications include oscillator upgrades, improved filtering, and various RF optimizations. The notable exception is the antenna switching arrangement around the MSi001 front-end, which is significantly easier to implement during the original hardware design phase than as a later modification.

As a result, the SDR RSP1 Simple represents a cost-optimized implementation of the Mirics SDR architecture, while the Full version demonstrates the maximum performance achievable from the same chipset with a more sophisticated RF design.

### Key Features

- Frequency coverage from approximately **10 kHz to 1 GHz**
- Five dedicated antenna inputs with fixed band-pass filters
- USB Type-C connectivity
- Up to **10 MHz instantaneous bandwidth**
- Variable ADC resolution from **8 to 14 bits**, depending on sample rate
- Based on the proven Mirics **MSi001 + MSi2500** SDR architecture

## Developer Notes

The complete SDR RSP1 Simple schematic is shown below and serves as the primary reference for development, troubleshooting, and PCB manufacturing.

![SDR schematics](https://raw.githubusercontent.com/gh4chris/msiSDR_starter/master/docs/schematics/schematics.jpg)

This design provides an affordable platform for SDR experimentation, amateur radio applications, signal analysis, and general-purpose RF reception while preserving compatibility with the original Mirics-based SDR ecosystem.

This is a Software Defined Radio (SDR) receiver PCB project based on the MSI2500 and MSI001 chips.

Use KiCad to view the project.

If you need to manufacture the PCB, just send the files from the gerber directory to a PCB factory.

It is recommended to have the factory do SMT assembly. Manual assembly can easily lead to soldering defects and reliability issues.

The recommended software is SDRuno using the SDRplay device profile.

The hardware is compatible with software designed for SDRplay-compatible receivers.

## Usage / Results

![Desktop](https://raw.githubusercontent.com/gh4chris/msiSDR_starter/master/images/2021-11-20_20h45_29.jpg).
![Setup](https://raw.githubusercontent.com/gh4chris/msiSDR_starter/master/images/usage.png).
