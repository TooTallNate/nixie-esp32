# Manufacturing settings

The PCB is designed for JLCPCB's published rigid-PCB capabilities as of
August 31, 2026.

## Order settings

- Layers: 6
- Material: FR-4
- Finished thickness: 1.6 mm
- Surface finish: ENIG (required by JLCPCB for 6+ layers)
- Outer copper: 1 oz
- Inner copper: 0.5 oz
- Solder mask: green
- Stackup: JLCPCB standard 6-layer 1.6 mm, no controlled-impedance requirement
- Via treatment: standard solder-mask tenting; do not select filled/capped
  via-in-pad processing. TP1-TP4 are intentionally exposed.

## Design limits

- Minimum track width: 0.1 mm, used only inside the USB-C connector courtyard
- Normal track width: 0.2 mm
- Minimum copper spacing: 0.1 mm, used only for package escapes
- Normal low-voltage spacing: 0.2 mm
- HV functional spacing: 0.5 mm
- Vias: 0.6 mm diameter with 0.3 mm finished drill
- Minimum copper-to-routed-edge clearance: 0.5 mm
- Minimum hole-to-copper clearance: 0.28 mm

The ESP32-S3 USB interface is USB 2.0 full-speed. Its short on-board route is
not ordered as controlled impedance. Use the JLCPCB DFM viewer on generated
Gerbers before releasing an order.

Capability reference:
https://jlcpcb.com/capabilities/pcb-capabilities

## Test points

Top-side probe pads expose the existing vias for these rails:

| Reference | Rail | Coordinate (mm) |
| --- | --- | --- |
| TP1 | GND | 165.913, 101.259 |
| TP2 | +3.3 V | 150.206, 100.959 |
| TP3 | +5 V | 161.300, 104.084 |
| TP4 | +170 V | 166.141, 119.890 |

TP4 is hazardous whenever the high-voltage supply is enabled. Use a suitably
rated probe and keep the board in an insulating fixture during measurement.
