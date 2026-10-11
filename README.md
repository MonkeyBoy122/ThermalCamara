# Pocket Thermal: handheld thermal camera

Hack Club Half-Life project, designed by Jeswanth Battula. Budget: under $100.

## What it is
A handheld thermal camera. An MLX90640 32x24 infrared array (wide-angle BAA version) feeds an ESP32-S3, which draws the heat image on a 2.0 inch ST7789 screen. It runs on a 603450 1200 mAh LiPo and charges over USB-C.

## Electronics (designed in EasyEDA)
- MLX90640ESF-BAA sensor (I2C, through-hole, bottom side)
- ESP32-S3-WROOM-1-N16R8 module with copper-free antenna keep-out
- 2.0 inch ST7789 LCD on an 8-pin header
- USB-C charging: TP4056 set to 600 mA (2 kOhm on PROG), DW01A + FS8205A battery protection, USBLC6 on the data lines, 5.1 kOhm CC resistors
- AP2112K 3.3 V regulator behind a slide power switch, battery-sense divider on IO4
- 3 buttons (reset, boot, trigger), 2 status LEDs, JST-PH battery connector
- Board: 92.44 x 115.81 mm, four 4 mm corner mounting holes
- The board cannot run from USB alone. The battery must be connected and switched on.

## Enclosure (CAD, built in code and exported to STEP)
Two-part screw-together shell: front bezel with LCD visor and button guard, back shell with a flared sensor horn, vents, chevron armor, lanyard eye, 1/4-20 tripod boss and accessory rail. Orange button caps, slider knob, trim ring and four TPU corner bumpers.

## Charging dock (CAD)
Camera leans back 12 degrees on its corner bumpers. An Apple USB-C plug sits in a tilted pocket under the camera's USB-C port. The base plate carries the cable groove, two stop posts, six screws and four foot pockets. Front name plate reads "Pocket Thermal" in Pacifico cursive.
Any standard 5 V USB charger works, including Apple and 65 W laptop chargers, with a USB-C to USB-C cable.

## Files (all in this one folder)
- dock_only.step, dock_with_camera_enclosure_and_cable.step: charging dock CAD
- enclosure_only.step, enclosure_with_board.zip: camera enclosure CAD
- PCB_layout_and_BOM_2026-10-10.pdf, Schematic_2026-10-06.pdf: board files
- figure12_3d_render.png, figure13_pcb_cad.png: board renders
- enclosure_*.png: finished enclosure pictures
- enclosure_build_hour01.png to hour13.png: enclosure build pictures
- dock_*.png: finished dock pictures
- dock_build_step1.png to step9.png: dock build pictures

## Open items before ordering the board
1. BOM: C2, C6, C7, C9, LED2, R5, R9, R10, R12 have no real LCSC part number. Reuse the sibling part numbers (C2 C19702, C7/C9 C1525, LED2 C2286, R5 C11702, R12 C25900) and look up C6 (1 uF) and R9/R10 (100 kOhm 0402).
2. Confirm the MLX90640ESF-BAA listing (C9900010874) can be ordered, and its price.
3. Check the sensor footprint pin order against the datasheet (1 SDA, 2 VDD, 3 GND, 4 SCL).
4. Check the LCD header order against your module.
5. With the N16R8 module, GPIO35, 36 and 37 are used internally. Keep them unconnected.
6. Check the 603450 battery connector polarity before plugging it in.
7. Assumed dimensions: LCD module, battery thickness, Apple plug (12.5 x 6.4 x 20 mm). Measure the real parts before printing.
8. Dock plug retention is by small ribs only. Test print and adjust.
