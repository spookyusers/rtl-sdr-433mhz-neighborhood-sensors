# RTL-SDR: 433 MHz Neighborhood Sensors (Princeton, NJ)

## Goal
Use RTL-SDR + rtl_433 to decode wireless devices transmitting on 433.92 MHz in my neighborhood:
- Outdoor weather stations (temp/humidity/rain)
- Tire pressure sensors (TPMS) from passing cars
- Garage door openers
- Other ISM band devices

## Hardware
- RTL-SDR dongle (generic/blog v3/v4?)
- Basic dipole antenna (adjustable)
- Setup: Indoors near window, dipole vertical, arms ~17cm for 433 MHz

## Software
- rtl_433 (built from source)
- OS: Ubuntu/Linux

## Installation Steps (Jan 8, 2026)
1. Installed dependencies:
   sudo apt install libtool libusb-1.0-0-dev librtlsdr-dev rtl-sdr cmake git build-essential pkg-config
2. Cloned and built rtl_433 in this directory

## Useful Commands
- Basic scan: `rtl_433`
- Verbose/all protocols: `rtl_433 -G`
- Specific frequency: `rtl_433 -f 433920000`
- Higher gain: `rtl_433 -g 40`
- Output to file: `rtl_433 -w output.csv` (or use -F json for better logging)

## Observations
- [Add notes here later as devices appear]
- Example: AcuRite sensor ID 123 → backyard neighbor?
- TPMS bursts during morning/evening commute

## Future Ideas
- Log data over time (temperature trends from neighbors)
- Filter specific device IDs
- Visualize with Python script