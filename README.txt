Helio-485 Rev A — KiCad layout

Open helio-485.kicad_pcb. KiCad 9 (file version 20241229).

Board: 140 x 178 mm, 2 layer, 1.6 mm, 2 oz. Two Keystone 1042 holders
are 88 mm long, so the 112 x 88 sketch could not hold them.

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
- The series midpoint is a 4 mm track on the right of the two holders.
- PACK- into the sense resistor and PACK+ into F1 are 2.5 mm tracks.
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
- USB-C faces +X after a 270 degree rotation. Nudge it to the edge you want.
- EN of the TPS61088 is GPIO23. It is not tied to the pack.
