# *Small* Board
**Parent Project**: [Modular Presepe Lights](../)

A configurable hardware board featuring **1 Intermittence Module** capable of driving **2 independent LED strings**. 

The flash period can be adjusted between approximately 5 and 20 seconds via trimmer `T1`. The individual light intensity of each string can be tuned using trimmers `T2` and `T3`. Through jumpers `J1` and `J2`, the intermittence oscillation can be selectively applied to none, one, or both of the LED driver channels.

![board-built](small-board_built.jpg)


## Schematic
![board-schematic](small-board_sch.jpg)


## PCB Layout
![board-pcb](small-board_pcb.jpg)


## Bill of Materials
### Prototyping & Connectors
- [x] 1 x Perfboard 3x7cm (10x24 holes)
- [x] 1 x DC Barrel Jack (PCB mount, 2.1mm)
- [x] 2 x 2-pin Screw Terminal Blocks (5mm pitch, for LED outputs)
- [x] 1 x 3-pin Male Header array (or 2-pin arrays for jumper selection)

### Integrated Circuits (ICs)
- [x] 1 x NE555 Timer IC (with socket)
- [x] 2 x LM317L 3-terminal adjustable linear regulators (TO-92 package)

### Resistors & Trimmers (1/4W, Standard Grade)
- [x] 2 x $47k\Omega$ resistors
- [x] 2 x $51\Omega$ resistors
- [x] 1 x $220k\Omega$ trimmer (for frequency tuning)
- [x] 2 x $1k\Omega$ trimmers (for LED intensity)

### Capacitors (25V rated or higher)
- [x] 1 x $47\mu F$ electrolytic capacitor
- [x] 1 x $10\mu F$ electrolytic capacitor
- [x] 1 x $100nF$ radial multilayer ceramic capacitor
- [x] 1 x $10nF$ polyester film (Mylar) capacitor
