## RF 50ohm Dummy Load

<p align="center">
<img src="./img/Dummy_Load_Device_IMG_1180.jpg" width="1000" height="600"/>
</p> 

## Credits

* Zygi SP5ELA for describing measurement methodology of HF transceiver output power.

## Design Overview

Presented RF Dummy Load shows aceptable SWR level (below 1.5) in the frequency range up to 500MHz. It is capable of withstanding up to 100W of power applied over up to 30sec time interval in ambient temperature of 26C. Theoretically calculated limit was in fact about 200W in ambient temperature of 26C, but this case was never verified in practice.
Design is based on inductance-less RFP-250 resistor manufactured by Anaren (or similar such as RFR 50-250).
This is rather mechanical then electronics project. The main challange was to ensure proper heat dissipation and keeping connections between resistor and UC1 socket as short as possible(in order to limit parasitic inductance).



<p align="center">
<img src="./meas/SVR_Dummy_Load_2024-03-31 12-53-41.png" width="400" height="400"/>

</p>

## Performance

Achieved dummy load performance is best described by the following graphs:

### VSWR Measurements for the frequency range of 10kHz-500MHz:

<p align="center">
<img src="./meas/SVR_Dummy_Load_2024-03-31 12-53-41.png" width="600" height="400"/>
</p>

### Derating Curve
This curve shows theoretically calculated time limits within, which dummy load can be safely subjected to given power levels. See Performace Evaluation section of this document for details.

<p align="center">
<img src="./sim/DeratingCurve_Simple 2024-03-31 220225.png" width="600" height="400"/>
</p>


### Smith Chart
Negligable amount of inductance visible in the measurements. For frequencies above 2m band (above 146MHz), effects of leakage capacitance starts to show. Acording to the manufacturer, leakage capacitance value is about 3pF.

<p align="center">
<img src="./meas/Smitch_Chart_Dummy_Load_2024-03-31 12-56-07.png" width="600" height="400"/>
</p>

The first measurement aimed to establish the temperature increase in Celcius per Watt of applied power. For each measurement point (power value), transmitter has been activated for the same duration of time $tdah$=15sec. Results has been summarized below:

<p align="center">
<img src="./sim/Temperature_vs_Power_Time 2024-03-31 215705.png" width="700" height="400"/>
</p>



## Characteristics Evaluation

### Measurement Setup

Simple digital thermometer was used to measure actual surface temperatures of the resistor: $tamb$ - resistor temperature when no power is applied to it and $tpwr$ - resistor temperature when given power is applied. The test setup used can be seen below:

<p align="center">
<img src="./img/Dummy_Load_temp_measurement_IMG_1172.jpg" width="600" height="400"/>
</p>


## References

[1] "???"