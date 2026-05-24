# Zenith
Zenith is a 75% (+ numpad!) wireless keyboard designed mainly for portability and ease of use. Based around the NRF52840, it works on ZMK firmware. 


## Hardware
Zenith's core hardware is straightforward. I'd categorize the hardware into 3 sections.
- The main matrix is where the actual key-scan occurs. Due to the Pro micro's low GPIO count, two shift registers are connected to the columns. The rows are on the main board itself. This is a standard COL2ROW layout :)
- For the LEDs, they are generic SK6812-Mini-E LEDs (Alternatively, you may use WS2812-Mini-V3J LEDs too). They are connected under the centre of each key. Due to the entire PCB being 3v3 but the LEDs being 5V, an MT3608 IC has been deployed to boost the voltage to the desired level. An inverter is also used to boost the 3v3 signal to 5V, but can be bypassed with a wire (since the first LED will also fix the signal on it's own).
- The miscellaneous components are the 2 encoders and the OLED. The OLED is optional, and not a part of the render due to my lack of ideas on how it could be used. However, the 2 encoders are used for media playback and volume control (and can be configured to control the RGB Matrix as well).

On the Numpad side of things, the main board is switched with a Xiao RP2040, although a Xiao NRF52840 + Battery can also be used without any changes to the PCB. A cutout under the Xiao has been provided if a battery is to be connected to the back of the board.
A normal 6x4 layout in the style of a numpad is used, along with RGB LEDs. This time, the 5V bus is provided to the LEDs via the USB VBUS, since the numpad is designed to be used in wired mode.

### Schematic
![schem 1](assets/schem/1.png)
![schem 2](assets/schem/2.png)
![macropad](assets/schem/3.png)
### PCB
![PCB](assets/PCB.png)
## Software
The main keyboard is built on ZMK firmware. The auxilary numpad is based on QMK since it's wired, but can be used witH ZMK if used with the Xiao NRF52840.

## Stackup
![stackup](assets/stackup.png)
|   |                                           |
|---|-------------------------------------------|
| 1 | Main Case (Battery Housing and Standoffs) |
| 2 | Charging Port Cover                       |
| 3 | Acrylic Plate                             |
| 4 | PCB, Switches and Keycaps                 |
| 5 | Middle Plate (Screw this!)                |
| 6 | Top Plate                                 |
| 7 | Top Cover                                 |

PCB screws are through the PCB into the main case. Plate screws are from the middle plate into the main case. Inserts are to be installed where shown in this image. 12 M3 inserts are needed in total. <br/>
![standoffs](assets/inserts.png)

## Renders
![main kb](assets/renders/main.png) <br/>
![covered kb](assets/renders/covered.png) <br/>
![macropad](assets/renders/macropad.png)

![magazine](assets/magazine.png)


## BOM

Here's a rough BOM of all the parts you'll need to recreate this project!

| Item               | URL                                                                                                                     | Cost       |
|--------------------|-------------------------------------------------------------------------------------------------------------------------|------------|
| PCB                | https://robu.in/                                                                                                        | 54         |
| Switches           | https://stackskb.com/store/akko-v3-matcha-green-pro-switch/                                                             | 35         |
| Acrylic Plate      | https://robu.in/                                                                                                        | 4          |
| Keycaps            | https://curiositycaps.in/products/green-black-gradient-cherry-side-backlit-keycaps                                      | 17         |
| Hotswap Sockets    | https://stackskb.com/store/gateron-hotswap-sockets/                                                                     | 11         |
| Diodes             | https://robu.in/product/1n4148-1w-zener-diode-pack-of-50/                                                               | 2          |
| LEDs               | (i alr have this)                                                                                                       | 12         |
| NRF52840 Pro Micro | https://robu.in/product/promicro-nrf52840-development-board/                                                            | 8          |
| Boost Converter    | https://robu.in/product/mt3608-xian-aerosemi-tech-boost-type-adjustable-2a-2v24v-sot-23-6-dc-dc-converters-rohs/        | 1          |
| Inductor           | https://robu.in/product/swpa5040s4r7nt-sunlord-4-7uh-30-3a-30-ohm-smd-5-0x5-0x4-0mm-power-inductors/                    | 1          |
| Filament           | https://india.numakers.com/products/pla-filament?variant=43307592286377                                                 | 10         |
| Shift Register     | https://robu.in/product/1-month-warranty-1354/                                                                          | 2          |
| Inverter           | https://robu.in/product/sn74hct14n-texas-instruments-logic-ic-inverter-hex-1-inputs-14-pins-dip-74hct14/                | <1         |
| Stabilizers        | https://stackskb.com/store/durock-clear-screw-in-stabilizers-v2/                                                        | 25         |
| Xiao RP2040        | (i alr have this)                                                                                                       | 5          |
| Fasteners, Inserts | (i alr have this)                                                                                                       | ~10        |
| Magnets            | (i alr have this)                                                                                                       | 5          |
|                    | TOTAL                                                                                                                   | 202        |
