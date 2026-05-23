# *Medium* Board
**Parent Project**: [Modular Presepe Lights](../)

A comprehensive controller board featuring **3 independent Intermittence Modules** capable of driving up to **5 LED strings**, alongside an integrated asymmetric **Firelight Module**.

The flash period of the three oscillators can be individually adjusted between approximately $5$ and $20$ seconds via trimmers `T1` through `T3`. Individual light intensity for the 5 channels is fine-tuned via trimmers `T4` to `T8`. The firelight subsystem provides dual outputs: one steady channel and one flickering channel (optimized for a combination of red and orange LEDs to emulate flame depth). Through jumpers `J1` to `J5`, each driver channel can be selectively connected to any or none of the intermittence modulation lines.

![board-built](medium-board_built.jpg)


## Schematic
![board-schematic](medium-board_sch.jpg)


## PCB Layout
![board-pcb](medium-board_pcb.jpg)


## Bill of Materials
### Prototyping & Connectors
- [x] 1 x Perfboard 7x9cm
- [x] 1 x DC Barrel Jack (male/female panel or PCB mount, 2.1mm)
- [x] 5 x 2-pin Screw Terminal Blocks (5mm pitch)
- [x] 1 x 3-pin Screw Terminal Block (5mm pitch, for Firelight outputs)
- [x] 1 x Multi-pin Male Header array (for jumper selection)

### Integrated Circuits & Discrete Semiconductors
- [x] 3 x NE555 Timer ICs
- [x] 5 x LM317 3-terminal adjustable linear regulators
- [x] 3 x General purpose NPN BJT Transistors (e.g., BC547 or similar low-current)
- [x] 1 x Small-signal Switching Diode (e.g., 1N4148)

### Resistors & Trimmers (1/4W, Standard Grade)
- [x] 6 x $47k\Omega$ resistors
- [x] 2 x $29k\Omega$ resistors
- [x] 1 x $6.8k\Omega$ resistor
- [x] 1 x $4.7\Omega$ resistor
- [x] 2 x $2.2k\Omega$ resistors
- [x] 1 x $1k\Omega$ resistor
- [x] 5 x $51\Omega$ resistors
- [x] 5 x $1k\Omega$ trimmers (for LED intensity tuning)
- [x] 3 x $220k\Omega$ trimmers (for frequency tuning)

### Capacitors (25V rated or higher)
- [x] 1 x $470\mu F$ electrolytic capacitor
- [x] 3 x $47\mu F$ electrolytic capacitors
- [x] 1 x $10\mu F$ electrolytic capacitor
- [x] 2 x $2.2\mu F$ electrolytic capacitors
- [x] 3 x $100nF$ capacitors
- [x] 3 x $10nF$ capacitors
