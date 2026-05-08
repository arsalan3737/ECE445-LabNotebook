
# Arsalan's Notebood
## *2026-01-27 Project Decided*
We spent the day brain storming what to do as our 445 senior design project. Below is some of our ideas
### Project Ideas

- HVAC Filter Replacement Detector
- Heated Mug
- Political Events World Map
- Regional Air Quality or Weather Map
- Ultrasonic Repeater for Water Usage
- Pill Separator with Robotic Arm
- Ping Pong Player Robotic Arm
- Water Filter Quality Detector
- SOS Pager
- Simple Smartwatch with SOS Feature
- Smart Band with Fall Detection
- Death Odor Detector
- Rotten Food Detector

We ended up doing a smart cane modular attachment will fall dectection object detection, and an app that would send and sms after falls and have haptic feedback for navigation using some sort of maps API.

## *2026-01-29 Proposal Submitted*

We created a proposal for an early extra-credit approval. We would like to include BLE, ESP32, haptic feedback, USB charging, high range battery, a lidar, as well as a TOF. The TOF would be used for fall detection, the lidar for object detection and ESP32 for the microcontoller as well as BLE for the andorid app.

## *2026-02-06 Allocation of Responsibilities*
Roles were decided, Eraad will handle the PCB and hardware, I will handle the BLE app and help Abdulrahman with the ESP32 code for fall dection as well as connecting BLE from the esp32 and app.

## *2026-02-17 Design and Practicality Discussion*
Eraad skectched what the final desing would look like as well as what general parts we would need. We started to research what the best possible IMU and we changed to use a TOF instead of a lidar due to restrictions in the class. 

## *2026-02-25 Researching Parts*
Eraad knew a lot about what parts we should use so he created this list with some power expectations:

- ESP32-S3-WROOM microcontroller: 3.6 V × 0.5 A = 1800 mW [1]
- ICM-20948 breakout board: 3.7 V × 9.5 mA = 35.15 mW [2]
- VL53L4CX breakout board: 3.3 V × 40 mA = 132 mW [3]
- 16000 RPM vibration motors: ∼ 100 mW each =∼ 200 mW [4]
- Red LED: 100 mW [5]
- Green LED: 100 mW [6]
- Passive draw: ∼ 10 mW (very large estimation)
- Quiescent draw: ∼ 10 mW (very large estimation)

Total: 2387.15 mW

the NiMH battery we were looking at is 12 V × 2000 mAh = 24000 mWH
which means that our system can run about little under 10hours with this battery at full power usage. 

Some optimistic parts we are looking at to potentially use in our design:
-  TBP4056A Charger IC
-  AP2112K-3.3TRG1 3.3 V Regulator
-  LTST-C171KGKT Green LED
-  LTST-C150CKT Red LED
-  CEM-1203_42 Buzzer (Potentially)
-  MicroUSB 10118194-0001LF (Micro-USB-B recepticle)

## *2026-03-04 Design Review and Changes*
We reviewed the design with our professor and TA. We learned a lot of the expectation of the presentations, like to introduce ourselves. We also changed to a LiPo battery as well as considering what could happen when falling. Componenet damage is important to consider.

## *2026-03-13 Breadboard Demo and Progress*
We spend this day mainly focusing on getting the fall detection working using and ESP32-WROOM-S3 dev board and the aforementioned IMU. We had some ideas on how to implement fall detection but we ended up using a state machine approach. We had 4 states NORMAL → FREEFALL → IMPACT → FALLEN. Normal would be normal use around 10m/s^2 while Freefall would be when its less thatn 5 m/s^2 for 20 samples, we polled at 100hz, Impact would be when it was greater than 100 and fallen is when it was at rest. 
<img width="1500" height="1999" alt="img4" src="https://github.com/user-attachments/assets/b3e27032-06d4-4d3b-86ab-ddd5b3f3a14e" />
