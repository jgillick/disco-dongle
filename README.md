# Disco Dongle

A USB to RS485 dongle uniquely designed for [Disco Bus](https://github.com/jgillick/Disco-Bus-Protocol)
networks, however, can be used for many other multidrop needs.

![3D Rendering](/resources/3D_render.png)

## About

This is a basic FTDI to RS485 device, that will connect your computer to a multidrop
network via USB. The RTS line is connected to RJ45 jack (ethernet jack) pin 3, and the DSR line is
connected to RJ45 jack pin 4.

If using this on a Disco Bus network, RTS/pin 3 would be to the first node's daisy chain line and
DSR/ping 4 would be on the shared signal line.

![Photo](/resources/photo.jpg)

## Ethernet Pinout

The output of the dongle to the bus, is via a RJ45 ethernet jack.

| RJ45 Pin | Connection    |
|----------|---------------|
| 1        | RS485 A/Y     |
| 2        | RS485 B/Z     |
| 3        | RTS / Daisy   |
| 4        | DSR / Signal  |
| 5        | GND           |
| 6        | GND           |
| 7        | Not connected |
| 8        | Not connected |

### RTS & DSR Lines

The `RTS` and `DSR` serial lines are broken out to RJ45 pins 3 and 4, respectively.
They are pulled up by a pair of 20k resistors, and assumed enabled when driven low.
They also have LEDs used to determine their enabled state. The LED for `RTS` is labeled
"D" (for Daisy) and `DSR` is labeled "S" (for Signal).

## Power over the bus

Since pins 7 and 8 are unused, these can be used to send power to the bus, while
using pins 5 and 6 for ground.

## BOM

| QTY | Designator  | Value    | Footprint | Description       | Digikey |
|-----|-------------|----------|-----------|-------------------|---------|
| 4   | R1,R2,R4,R3 | 200      | 0805      | Resistor          | [RMCF0805JT200RCT-ND](https://www.digikey.com/product-detail/en/stackpole-electronics-inc/RMCF0805JT200R/RMCF0805JT200RCT-ND/1942543) |
| 3   | R5,R6,R8    | 20k      | 0805      | Resistor          | [311-20KARCT-ND](https://www.digikey.com/product-detail/en/yageo/RC0805JR-0720KL/311-20KARCT-ND/731229) |
| 1   | R7          | 120      | 0805      | Resistor          | [RMCF0805JT120R](http://www.digikey.com/product-detail/en/stackpole-electronics-inc/RMCF0805JT120R/RMCF0805JT120RCT-ND/1942540) |
| 3   | C1,C4,C5    | 100nF    | 0805      | Capacitor         | [1276-2450-1-ND](http://www.digikey.com/product-detail/en/samsung-electro-mechanics-america-inc/CL21B104MBCNNNC/1276-2450-1-ND/3890536) |
| 1   | C2          | 4.7uF    | 0805      | Capacitor         | [1276-6463-1-ND](http://www.digikey.com/product-detail/en/samsung-electro-mechanics-america-inc/CL21A475KOFNNNG/1276-6463-1-ND/5958091)|
| 1   | C3          | 10nF     | 0805      | Capacitor         | [1276-2434-1-ND](http://www.digikey.com/product-detail/en/samsung-electro-mechanics-america-inc/CL21B103KAANNNC/1276-2434-1-ND/3890520) |
| 2   | D1,D2       |          | 0805      | TX/RX LEDs        | [475-1415-1-ND](http://www.digikey.com/product-detail/en/osram-opto-semiconductors-inc/LH-R974-LP-1/475-1415-1-ND/1802604) |
| 2   | D3,D4       |          | 0805      | Daisy/Signal LEDs | [475-1410-1-ND](http://www.digikey.com/product-detail/en/osram-opto-semiconductors-inc/LG-R971-KN-1/475-1410-1-ND/1802598) |
| 1   | U1          |          | SSOP-28   | FT232RL           | [768-1007-1-ND](http://www.digikey.com/product-detail/en/ftdi-future-technology-devices-international-ltd/FT232RL-REEL/768-1007-1-ND/1836402) |
| 1   | U2          |          | SOIC-8    | RS485 Transceiver | [ISL81487EIBZ-TCT-ND](http://www.digikey.com/product-detail/en/intersil/ISL81487EIBZ-T/ISL81487EIBZ-TCT-ND/1034270) |
| 1   | J1          |          |           | USB - B           | [ED2983-ND](http://www.digikey.com/product-search/en?keywords=USB-B1HSB6) |
| 1   | J2          |          |           | RJ45 Jack         | [609-1046-ND](http://www.digikey.com/product-search/en?keywords=54602-908LF) |


## Order One

You can either build one yourself, of [MacroFab](http://macrofab.com) will assemble
one for you for ~$30.

To use MacroFab:

 * [Create an account](http://macrofab.com)
 * Create a new PCB
 * Goto the "Design Files" tab.
   * Upload `kicad/DiscoDongle.kicad_pcb`
   * Upload `BOM_MacroFab.xyrs`
 * Verify all parts are selected/populated on the "Bill of Materials" Tab.
 * Verify parts are arranged properly on "Placement" tab.
 * Click "Order Now"

## Credit

 This hardware was adapted from the [original work](https://github.com/cinderblock/DanceDongle)
 by [Cameron Tacklind](https://github.com/cinderblock).