Helio-485 Rev A — KiCad layout

Open helio-485.kicad_pcb. KiCad 9 (file version 20241229).

Board: 140 x 178 mm, 2 layer, 1.6 mm, 2 oz. Two Keystone 1042 holders,
2S, 3500 mAh cells. Three cells is the maximum that was allowed, and
three still cannot make 48 h on a GEM2, so the pack stays 2S. The
TP5100 and the S-8252 are 2-cell parts.

What is already done
- Official KiCad footprints for the holders, USB-C (HRO TYPE-C-31-M-12),
  Phoenix 5.08 mm terminals, SOT-23, SOT-23-6, SOIC-8, QFN-16, TO-252,
  TO-92, and the passives.
- ESP32-C5-WROOM-1 land from the Espressif pattern: 1.27 mm pitch,
  1.5 x 0.9 mm pads, row centers at ±8.0 mm, pad column span 16.51 mm,
  antenna at +Y. Pin 1 is the antenna-end pad on the left, marked with a dot.
- TPS61088 RHL0020A land from TI drawing 4219071. Pin 1 is the bottom-left
  pad. The exposed pad is pin 21 (PGND).
- Nets on every placed pad.
- The series midpoint is a 2.5 mm track on the right of the two holders.
- PACK- into the sense resistor and PACK+ into F1 are 2 mm tracks.
- Back copper is a GND zone. Press B to fill it.
- Antenna keepout is a rule area on both layers at the top-right. No copper.

What you still route
Everything else is a ratsnest. Do that in pcbnew, then run DRC.
Do not run Update PCB from Schematic. There is no schematic in this
project; the nets live on the board.

Check before you fab
- S-8252 pin numbers are the SOT-23-6 table: 1 DO, 2 CO, 3 VM, 4 VC,
  5 VDD, 6 VSS. VDD is the top of the stack.
- TP5100 pin numbers follow the datasheet grouping used on the rev A
  sheet (VIN on 1/4/5/16, LX on 2/3, BAT on 9). Confirm against the reel.
- AO3401A is G/S/D = pins 1/2/3. AOD510 is G/D/S = 1/2/3, tab is drain.
- USB-C (J4, HRO TYPE-C-31-M-12) is on the left edge, plug facing out.
  D+ / D− go through 22 Ω (Rdp, Rdm) to module pins 14 and 13
  (GPIO14 USB D+, GPIO13 USB D−). CC1 and CC2 are 5.1 kΩ to GND.
  D3 (B5819W, SOD-123 pin 1 = cathode) ORs VBUS onto VSYS so the
  3.3 V buck runs from the laptop when the pack is out. USB does not
  charge the cells. Full-speed only; the pair is not 90 Ω.
- USB-C programs the ESP32. J2 is the GEM2 supply: pin 1 yellow, pin 2 purple.
  J3 is Modbus: A pink, B green. The meter wants external power for Modbus.
