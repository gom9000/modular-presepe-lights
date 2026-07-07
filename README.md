# Modular Presepe Lights
**Type**: Standalone Project | **Status**: Completed

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

Standard low-current LEDs typically operate optimally within a current range of $2mA$ to $20mA$. In the board implementations, $R_s$ is realized using a fixed $51\ \Omega$ safety resistor in series with a $1\text{ k}\Omega$ tuning trimmer to safely clamp the maximum current and allow continuous brightness adjustment.

In the worst-case operating scenario, with a maximum supply voltage of $V_{in} = 15\text{V}$, a single red LED ($V_f \approx 2\text{V}$), and the driver tuned to $I_{out} = 20\text{ mA}$, the power dissipation ($P_{LM317}$) and the resulting junction temperature ($T_j$) and case temperature ($T_c$) of the regulator in a TO-92 package ($\theta_{ja} = 160^\circ\text{C/W}$, $\theta_{jc} = 80^\circ\text{C/W}$) are calculated as follows:

$$P_{LM317} = (V_{in} - 1.25\text{V} - V_f) \cdot I_{out} = (15\text{V} - 1.25\text{V} - 2\text{V}) \cdot 0.02\text{A} = 235\text{ mW}$$

$$T_j = T_a + (P_{LM317} \cdot \theta_{ja}) = 25^\circ\text{C} + 0.235\text{W} \cdot 160^\circ\text{C/W} \approx 63^\circ\text{C}$$

$$T_c = T_a + (P_{LM317} \cdot \theta_{jc}) = 25^\circ\text{C} + 0.235\text{W} \cdot 80^\circ\text{C/W} \approx 45^\circ\text{C}$$

#### Test Validation
To validate the thermal behavior under continuous operation, a stress test was performed on tiny board, with $V_{in} = 15\text{V}$, a single LED ($V_f = 2.2\text{V}$), and the driver tuned to max $I_{out} = 24.3\text{ mA}$ ($P_{LM317} \approx 0.28\text{ W}$). After 20 minutes, the TO-92 plastic body reached a stable thermal equilibrium at **$53^\circ\text{C}$** (at room temperature $\sim 27^\circ\text{C}$).


### Intermittence Module
* **Role:** Square-wave low-frequency oscillator for blinking effects.
* **Implementation:** A standard NE555 timer configured as an astable multivibrator. It delivers a rectangular voltage output of approximately $V_{out} \approx V_{cc} - 1.5V$.

![image](resources/intermittence-module-schematic.jpg)

The timing parameters are defined by:

$$period = 0.69 \cdot (R_1 + 2R_2) \cdot C$$

$$duty\_cycle = \frac{R_1 + R_2}{R_1 + 2R_2}$$

In the board implementations: $R_1 = 47K\Omega$, $R_2 = 47K\Omega \text{ (fixed)} + 220K\Omega \text{ (trimmer)}$ and $C_1 = 47\mu F$.
This specific dimensioning yields a tuning window of $\sim 5$ to $20$ seconds per complete cycle, while keeping the duty cycle close to a symmetrical look ($\sim 50\% - 60\%$) across the entire adjustment range.


### Firelight Module
* **Role:** Irregular flickering effect to simulate real flame or embers.
* **Implementation:** A fixed-frequency astable multivibrator "disturbed" by a secondary, simple relaxation oscillator. The interaction between the two asymmetric wave frequencies creates a realistic, pseudo-random tremolo effect.

![image](resources/firelight-module-schematic.jpg)

In the board implementations, resistors and capacitors components are sized to run the multivibrator at a baseline frequency of $\sim 10\text{ Hz}$. The secondary oscillator generates a much slower relaxation curve running above $1\text{ Hz}$.

### Starlight Module
* **Role:** Shimmering stars effect.
* **Implementation:** Uses the exact same chaotic dual-oscillator topology as the *Firelight Module*, but tuned with a slightly higher frequency to mimic distant starlight scintillation.


### LED string Module
* **Role:** Light emitter arrays (up to 4–5 small-current LEDs in series).
* **Implementation:** The total cumulative forward voltage drop ($V_f$) of the string must remain lower than the driver's available $V_{out}$.

![image](resources/led-string-module-schematic.jpg)

Typical, but very very indicative, forward voltage drops ($V_f$) across standard LED colors are:
* **Red:** $\sim 1.8\text{V} - 2.0\text{V}$
* **Orange / Yellow:** $\sim 2.0\text{V}$
* **Green:** $\sim 1.9\text{V} - 4.0\text{V}$
* **Blue:** $\sim 2.5\text{V} - 3.7\text{V}$
* **White:** $\sim 3.2\text{V} - 4.0\text{V}$


## Hardware Form Factors (Boards)
The modular blocks are deployed across three physical board layouts, depending on the complexity of the scenery:

* **[Tiny Board](boards/tiny-board):** Implements a compact, single-line, configurable intermittence board.
* **[Small Board](boards/small-board):** A configurable board featuring 1 Intermittence Module capable of driving 2 independent LED strings.
* **[Medium Board](boards/medium-board):** A complete controller housing 3 Intermittence Modules capable of driving up to 5 independent LED strings, plus a dedicated Firelight generator.



## About & License
**Author:** Alessandro Fraschetti (gom9000).  
**Technical Notes:** All hardware design, schematics, and layouts were developed using the free **ExpressPCB** CAD suite, supported by the custom **[expresspcb-goslib](https://github.com/gom9000/expresspcb-goslib)** asset library.  
**License:** This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and distribute it. Credit in your derivative documentation is highly appreciated.