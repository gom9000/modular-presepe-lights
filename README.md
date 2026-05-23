# Modular Presepe Lights
**Type**: Modular Lighting / Project | **Status**: Completed

A set of simple modular, low-current, lighting controllers designed for the presepe lighting. 

The system drives small LED strings using linear and analog blocks powered by an external $12VDC$ to $15VDC$ supply.
The modular architecture allows cells to be combined depending on the specific scenic requirements (e.g., steady light, flickering fire, or blinking stars).

![overview](resources/overview.jpg)


## Specifications
* **Input Voltage:** $12VDC$ to $15VDC$ (external DC adapter).
* **Architecture:** Modular blocks (Drivers, Oscillators, LED Strings).
* **Max Load:** Designed for low-current, short LED strings (typically up to 4–5 LEDs per string, depending on total forward voltage drop).


## Modules

### LED Driver Module
* **Role:** Constant Current Source (Mandatory block).
* **Implementation:** Built around a classic LM317 linear regulator. It is able to drive a LED string that has a total voltage drop of less than $V_{in}$ minus the regulator's dropout voltage.

![image](resources/led-driver-module-schematic.jpg)

The regulated output current is defined by:

$$I_{out} = \frac{1.25}{R_s}$$


### Intermittence Module
* **Role:** Square-wave low-frequency oscillator for blinking effects.
* **Implementation:** A standard NE555 timer configured as an astable multivibrator. It delivers a rectangular voltage output of approximately $V_{out} \approx V_{cc} - 1.5V$.

![image](resources/intermittence-module-schematic.jpg)

The timing parameters are defined by:

$$period = 0.69 \cdot (R_1 + 2R_2) \cdot C$$

$$duty\_cycle = \frac{R_1 + R_2}{R_1 + 2R_2}$$


### Firelight Module
* **Role:** Irregular flickering effect to simulate real flame or embers.
* **Implementation:** A fixed-frequency astable multivibrator "disturbed" by a secondary, simple relaxation oscillator. The interaction between the two asymmetric wave frequencies creates a realistic, pseudo-random tremolo effect.

![image](resources/firelight-module-schematic.jpg)


### Starlight Module
* **Role:** Shimmering stars effect.
* **Implementation:** Uses the exact same chaotic dual-oscillator topology as the *Firelight Module*, but tuned with a slightly higher frequency to mimic distant starlight scintillation.


### LED string Module
* **Role:** Light emitter arrays (up to 4–5 small-current LEDs in series).
* **Implementation:** The total cumulative forward voltage drop ($V_f$) of the string must remain lower than the driver's available $V_{out}$.

![image](resources/led-string-module-schematic.jpg)

Typical, but very very indicative, forward voltage drops ($V_f$) across standard LED colors are:
* **Red:** $\sim 1.6\text{V} - 2.0\text{V}$
* **Orange / Yellow:** $\sim 2.0\text{V}$
* **Green:** $\sim 1.9\text{V} - 4.0\text{V}$
* **Blue:** $\sim 2.5\text{V} - 3.7\text{V}$
* **White:** $\sim 3.2\text{V} - 4.0\text{V}$


## Hardware Form Factors (Boards)
The modular blocks are deployed across three physical board layouts, depending on the complexity of the scenery:

* **[Tiny Board](boards/tiny-board):** Implements a compact, single-line, configurable intermittence board.
* **[Small Board](boards/small-board):** A configurable board featuring 1 Intermittence Module capable of driving 2 independent LED strings.
* **[Medium Board](boards/medium-board):** A complete controller housing 3 Intermittence Modules (up to 5 LED strings per module) plus a dedicated Firelight generator.



## About & License
**Author:** Alessandro Fraschetti (gom9000).  
**Technical Notes:** All hardware design, schematics, and layouts were developed using the free **ExpressPCB** CAD suite, supported by the custom **[expresspcb-goslib](https://github.com/gom9000/expresspcb-goslib)** asset library.  
**License:** This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and distribute it. Credit in your derivative documentation is highly appreciated.