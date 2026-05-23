# *Tiny* Board
**Parent Project**: [Modular Presepe Lights](../)

A highly compact, single-channel hardware deployment featuring **1 Intermittence Module** capable of driving **1 LED string**.

The flash period can be adjusted between approximately $5$ and $20$ seconds via trimmer `T1`, while the individual light intensity of the string is fine-tuned using trimmer `T2`. The intermittence modulation can be entirely enabled or disabled via jumper `J1` to allow for steady-light operation when needed.

![board-built](tiny-board_built.jpg)


## Schematic
![board-schematic](tiny-board_sch.jpg)


## PCB Layout
![board-pcb](tiny-board_pcb.jpg)


## Bill of Materials
### Prototyping & Connectors
- [x] 1 x Perfboard 2x8cm
- [x] 1 x DC Barrel Jack (male/female panel or PCB mount, 2.1mm)
- [x] 1 x 2-pin Screw Terminal Block (5mm pitch)
- [x] 1 x 2-pin Male Header (for jumper selection)

### Integrated Circuits (ICs)
- [x] 1 x NE555 Timer IC
- [x] 1 x LM317 3-terminal adjustable linear regulator

### Resistors & Trimmers (1/4W, Standard Grade)
- [x] 2 x $47k\Omega$ resistors
- [x] 1 x $51\Omega$ resistor
- [x] 1 x $1k\Omega$ trimmer (for LED intensity tuning)
- [x] 1 x $220\Omega$ trimmer (for frequency tuning)

### Capacitors (25V rated or higher)
- [x] 1 x $47\mu F$ electrolytic capacitor
- [x] 1 x $10\mu F$ electrolytic capacitor
- [x] 1 x $100nF$ capacitor
- [x] 1 x $10nF$ capacitor
