# Zenith
Zenith is a 75% (+ numpad!) wireless keyboard designed mainly for portability and ease of use. Based around the NRF52840, it works on ZMK firmware. 


## Hardware
Zenith's core hardware is straightforward. I'd categorize the hardware into 3 sections.
- The main matrix is where the actual key-scan occurs. Due to the Pro micro's low GPIO count, two shift registers are connected to the columns. The rows are on the main board itself. This is a standard COL2ROW layout :)
- For the LEDs, they are generic SK6812-Mini-E LEDs (Alternatively, you may use WS2812-Mini-V3J LEDs too). They are connected under the centre of each key. Due to the entire PCB being 3v3 but the LEDs being 5V, an MT3608 IC has been deployed to boost the voltage to the desired level. An inverter is also used to boost the 3v3 signal to 5V, but can be bypassed with a wire (since the first LED will also fix the signal on it's own).
- The miscellaneous components are the 2 encoders and the OLED. The OLED is optional, and not a part of the render due to my lack of ideas on how it could be used. However, the 2 encoders are used for media playback and volume control (and can be configured to control the RGB Matrix as well).

On the Numpad side of things, the main board is switched with a Xiao RP2040, although a Xiao NRF52840 + Battery can also be used without any changes to the PCB. A cutout under the Xiao has been provided if a battery is to be connected to the back of the board.
A normal 6x4 layout in the style of a numpad is used, along with RGB LEDs. This time, the 5V bus is provided to the LEDs via the USB VBUS, since the numpad is designed to be used in wired mode.

## Software
The main keyboard is built on ZMK firmware. The auxilary numpad is based on QMK since it's wired, but can be used witH ZMK if used with the Xiao NRF52840.

## Stackup
![stackup](assets\stackup.png)
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
![standoffs](assets\inserts.png)

## Renders
![main kb](assets\renders\main.png) <br/>
![covered kb](assets\renders\covered.png) <br/>
![macropad](assets\renders\macropad.png)

![magazine](assets\magazine.png)


## BOM

Here's a rough BOM of all the parts you'll need to recreate this project!

|--------------------|------------------------------------------------------------------------------------|------------|
| PCB                | https://robu.in/                                                                   | 54         |
| Switches           | https://stackskb.com/store/akko-v3-matcha-green-pro-switch/                        | 35         |
| Acrylic Plate      | https://robu.in/                                                                   | 4          |
| Keycaps            | https://curiositycaps.in/products/green-black-gradient-cherry-side-backlit-keycaps | 17         |
| Hotswap Sockets    | https://stackskb.com/store/gateron-hotswap-sockets/                                | 11         |
| Diodes             | https://robu.in/                                                                   | 2          |
| LEDs               | https://etstore.in/                                                                | 12         |
| NRF52840 Pro Micro | https://robu.in/                                                                   | 8          |
| Boost Converter    | https://robu.in/                                                                   | 1          |
| Inductor           | https://robu.in/                                                                   | 1          |
| Filament           | https://india.numakers.com/                                                        | 10         |
| Shift Register     | https://robu.in/                                                                   | 2          |
| Stabilizers        | https://stackskb.com/store/durock-clear-screw-in-stabilizers-v2/                   | 25         |
| Xiao RP2040        | https://robu.in/                                                                   | 5          |
| Fasteners, Inserts | https://onlyscrews.in/                                                             | ~10        |
| Magnets            | https://onlyscrews.in/                                                             | 5          |
|                    | TOTAL                                                                              | 202        |
