# SN74141 GPIO and digit mapping

Each tube uses one SN74141N with four ESP32-S3 GPIOs connected directly to
its TTL-compatible BCD inputs.

| Tube | A (LSB) | B | C | D (MSB) |
| --- | --- | --- | --- | --- |
| N1 / U4 | GPIO1 | GPIO2 | GPIO5 | GPIO6 |
| N2 / U5 | GPIO7 | GPIO12 | GPIO13 | GPIO14 |
| N3 / U6 | GPIO17 | GPIO18 | GPIO21 | GPIO38 |

The decoder outputs are permuted to minimize PCB trace crossings. Firmware
must translate the desired displayed digit to the following BCD code:

| Displayed digit | BCD code |
| --- | --- |
| 0 | 7 |
| 1 | 9 |
| 2 | 8 |
| 3 | 0 |
| 4 | 1 |
| 5 | 5 |
| 6 | 4 |
| 7 | 6 |
| 8 | 3 |
| 9 | 2 |

BCD values 10 through 15 blank the SN74141 outputs.

## Assembly wire links

Install these five insulated point-to-point wires after soldering the IC
sockets and Nixie tubes. Keep the cathode wires separated from low-voltage
conductors; they switch the tube's +170 V domain.

| Link | From | To | Signal |
| --- | --- | --- | --- |
| W1 | U2 pad 10 | U6 pin 3 | GPIO17 / N3 BCD A |
| W2 | U5 pin 9 | N2 pin 3 | N2 cathode K3 |
| W3 | U5 pin 13 | N2 pin 4 | N2 cathode K4 |
| W4 | U6 pin 13 | N3 pin 4 | N3 cathode K4 |
| W5 | PS1 pin 3 | R12 pad 2 | +170 V anode bus |

Use appropriately rated insulated wire for W5 and route it along the right
board edge, away from low-voltage conductors.

The PCB has no holes or copper pads for the IN-14 `LHDP` and `RHDP` leads.
Snip both unused decimal-point leads before installing each tube.
