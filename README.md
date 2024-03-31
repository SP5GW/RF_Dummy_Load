## RF 50ohm Dummy Load

<p align="center">
<img src="./img/Dummy_Load_Device_IMG_1180.jpg" width="1000" height="600"/>
</p> 

## Credits

* Zygi SP5ELA for describing measurement methodology of HF transceiver output power.

## Design Overview

Presented RF Dummy Load shows aceptable SWR level (below 1.5) in the frequency range up to 500MHz. It is capable of withstanding up to 100W of power applied over up to 30sec time interval in ambient temperature of 26C. Theoretically calculated limit was in fact about 200W in ambient temperature of 26C, but this case was never verified in practice.
Design is based on inductance less RFP-250 resistor manufactured by Anaren (or similar).
This is rather mechanical then electronics project. The main challange was to ensure proper heat dicipation and keeping connections between resistor and UC1 socket as short as possible.



## Circuit Simulations

To be able to relate simulation results to NanoVNA measurements the first step is to establish measurement correction, which Nanovna calculates as part of calibration process.

<p align="center">
<img src="./sim/S21CalibrationResult.png" width="400" height="400"/>
</p>

As can be seen from the results above, in our case the calibration correction is +6dB, which is added to all measurement results.

Now we can simulate RF Tap attenuation levels for unterminated and terminated with 50ohm resistor RF Paths:

<p align="center">
<img src="./sim/S21SimulationResults.png" width="1000" height="700"/>
</p>

In case of unterminated RF Path attenuation of RF Tap is equal -34dB and when the RF Path is terminated with 50ohm load attenuation increases to -40dB. 

As can be seen in Measurements section simulation results match perfectly actual measurements.

Simulation of the impact of parasitic capacitance present in the circuit and effect of corrective capacitance added in parallel to resistor R1 can be found below:

<p align="center">
<img src="./sim/S21SimulationResults_FrequencyDependingLoss.png" width="1000" height="700"/>
</p>

Finally, calculations of resistor power ratings is given below (simulation run for peak power value of 100W):

<p align="center">
<img src="./sim/ResistorPowerRatingSimulation.png" width="1000" height="700"/>
</p>

## Measurements

### Device frequency response measured between one of RF path ends and RF tap output (another RF path end is terminated with 50ohm dummy load)

<p align="center">
<img src="./meas/S21_RF_Input_RF_Tap_noCap_50ohmTerm_2024-03-03 11-27-41.png" width="400" height="400"/>
<img src="./meas/S21_RF_Input_RF_Tap_withCap_50ohmTerm.png" width="400" height="400"/>
</p>

Picture to the right shows RF Tap's S21 curve when capaitor C is present. 
Picture to the left shows Tap's S21 curve when capacitor C is not present. 
The cap C reduces attenuation for signals above 144MHz.

### VSWR measured at one of RF path ends (another RF path end is terminated with 50ohm dummy load)

<p align="center">
<img src="./meas/VSWR_RF_Input_noCap_50ohmTerm_2024-03-03 11-19-03.png" width="400" height="400"/>
<img src="./meas/VSWR_RF_Input_RF_Tap_withCap_50ohmTerm_2024-03-03 12-27-44.png" width="400" height="400"/>
</p>

Picture to the right shows RF Tap's VSWR curve measured at RF input for device with capaitor C.
Picture to the left shows Tap's VSWR curve measured at RF input for device with no capacitor C.
In both cases other end of RF path is terminated with 50 ohm dummy load.
It can be observed that while capacitor C improves Tap's frequency response seen from Tap output (attenuation is closer to -40dB accross enntire band) it also slightly increases VSWR measured at one of RF path ends.


### Insertion loss measured at RF path ends (RF Tap termination does not impact measurements)

<p align="center">
<img src="./meas/S21_RF_Input_RF_Input_noCap_2024-03-03 11-49-04.png" width="300" height="300"/>
</p>

Insertion loss caused by RF Tap is not greater then -0.5dB accross entire band (DC-500MHz). Presence of Cap does not impact insertion loss level in any significant way.
RF Tap termination does not impact measurement results i.e. insertion loss is the same for RF Tap output terminated with 50ohm resistor and when RF Tap is left open.

## RF Tap adaptation to high impedance measurement device such as scope

When Tap is connected to high impedance measurement device such as scope with input impedance equal or higher then 1Mohm, its resistor R3 shown on the diagram below has to be doubled in value (increase from 2.5kohm to 5kohm) in order to maintain desired level of attenuation (-40dB / 1:100 Voltage attenuation). 
Simulation results: 

<p align="center">
<img src="./sim/RF_Tap_Modification_For_Scope.png" width="400" height="400"/>
</p>

Actual voltage measurements, input voltage supplied from functional generator (50ohm output impedance):

<p align="center">
<img src="./meas/RF_Tap_Scope_Adaptation_DSO_2024-03-31 20-39-00.png" width="400" height="400"/>
</p>

In practice resistor R3 is series of 2x820ohm resistors and 5k precission potentiometer. 
## References

[1] "Simple RF-Power Measurement", QST June 2001 by Wes Hayward W7ZOI and Bob Larkin W7PUA

[2] "Ten Essential Skills for Electrical Engineers" by Barry L. Dorr, Willey 2014, Chapter: "How to Design Resistive Circuits"