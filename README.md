# RTL-SDR: 433 MHz Neighborhood Sensors (Princeton, NJ)

**January 2026 – Ongoing**

## Goal
Use RTL-SDR + rtl_433 to decode 433.92 MHz wireless devices transmitting in my neighborhood:
- Outdoor/indoor weather stations (temperature, humidity)
- Tire pressure sensors (TPMS) from passing cars
- Garage door openers / remote controls
- Soil moisture probes, security sensors, and other ISM band devices

## Hardware
- RTL-SDR dongle (RTL-SDR Blog V4 detected)
- Basic adjustable dipole antenna
- Setup: Indoors near window, dipole oriented vertically, arms adjusted to ~17 cm for 433 MHz

## Software
- rtl_433 (built from source, latest master as of January 8, 2026)
- OS: Ubuntu/Linux

## Software Installation
Built and installed rtl_433 from source:

```bash
sudo apt install libtool libusb-1.0-0-dev librtlsdr-dev rtl-sdr cmake git build-essential pkg-config
git clone https://github.com/merbanan/rtl_433.git
cd rtl_433
mkdir build && cd build
cmake ..
make
sudo make install
sudo ldconfig
```

Source: https://github.com/merbanan/rtl_433

## Useful Commands
- Basic scan: `rtl_433`
- Specific frequency: `rtl_433 -f 433920000`
- Higher gain: `rtl_433 -g 40`
- Output to file: `rtl_433 > output.log` (or `-F json` for structured logging)

## Initial Captures (January 8, 2026)
Successfully decoded a variety of real-world 433 MHz devices from nearby homes:

- Multiple **VAUNO EN8822C** indoor temperature/humidity sensors (22–24.5°C, 65–74% RH)
- Outdoor/cold sensors:
  - Acurite-609TXC: 6.4°C
  - Oregon-SL109H: 0.0°C
  - GT-WT02: 0.0°C, 32% RH
- **Springfield-Soil** probes:
  - One unusually hot: 51.2°C (likely indoors- greenhouse?)
  - One frozen: 0.2°C, 0% moisture (winter soil?)
- **DSC Security** wireless door/window contact (closed, no activity/tamper)

Full raw log: [neighborhood_sensors_2026-01-08.log](neighborhood_sensors_2026-01-08.log)