# arduino-parkingsensor
This project is an automated, automotive-style proximity alert system. It delivers real-time visual and audible distance tracking using an HC-SR04 ultrasonic sensor, a tri-color LED array (Green, Yellow, Red), and a piezo audio indicator controlled by an Arduino microcontroller.
#System Specifications
Parameter Specification / Range Notes
Microcontroller Platform
Arduino Architecture (5V
TTL)
Compatible with Uno, Nano, Mega
System Input Voltage 5.0 VDC ± 10% Supplied directly via Arduino 5V rail
Maximum Operating
Current
~55 mA
Peak draw when Red LED & Buzzer are
engaged
Standby Current ~17 mA Base draw when only Green LED is active
Effective Detection Range 2.0 cm to 300.0 cm Software-optimized tracking range
Detection Angle < 15° Conical field Optimal reflection on flat, solid surfaces
Audio Indicator Output Continuous / Pulsed Beep Piezoelectric transducer output

#Component Pin Mapping & Hardware Connections
Component
Component
Pin
Arduino IO
Pin
Function / Description
HC-SR04
Sensor
VCC 5V Core +5V power supply
Trig Pin 9 Input: Trigger pulse (10 microseconds)
Echo Pin 10 Output: Echo travel time response pulse
GND GND Shared common system ground
Green LED Anode (+) Pin 5 Safe Zone indicator (Requires 220Ω resistor)
Yellow LED Anode (+) Pin 6
Warning Zone indicator (Requires 220Ω
resistor)
Red LED Anode (+) Pin 7
Danger Zone indicator (Requires 220Ω
resistor)
Piezo Buzzer Positive (+) Pin 3 Acoustic notification alert output
All Commons Cathodes (-) GND Return path to system ground

#Operational Logic & Threshold Profiles
The system continuously samples proximity calculations to dynamically scale indicator responses across
three logical alert zones:
🟢 Safe Zone (> 50.0 cm):
Visual: Green LED ON | Yellow LED OFF | Red LED OFF
Audio: Buzzer OFF (Completely Silent)
🟡 Warning Zone (21.0 cm to 50.0 cm):
Visual: Green LED OFF | Yellow LED ON | Red LED OFF
Audio: Intermittent rapid pulsing beeps (80 ms ON / 80 ms OFF)
🔴 Danger Zone (0.0 cm to 20.0 cm):
Visual: Green LED OFF | Yellow LED OFF | Red LED ON
Audio: 100% continuous, uninterrupted solid alarm tone
NOTE: YOU CAN EDIT THE DISTANCE AS YOU LIKE

#Mathematical Distance Formula
The embedded application calculates distance based on the speed of sound through ambient air at room
temperature (~20°C):
Because the sensor evaluates total round-trip flight time (pulse exit to echo return), the software divides
the raw microsecond reading by 2 to solve for the linear distance to the obstacle:
HUSSEIN ATTIE
Speed of Sound ≈ 343 m/s = 0.0343 cm/µs
Distance (cm) =
2
Echo Duration Time (µs) × 0.0343

THE SKETCH FILE IS IN TAGS 

THANKS FOR SUPPORTING AND STAY TUNED FOR NEW PROJECTS!!!
