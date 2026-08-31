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

The PCB has no holes or copper pads for the IN-14 `LHDP` and `RHDP` leads.
Snip both unused decimal-point leads before installing each tube.
