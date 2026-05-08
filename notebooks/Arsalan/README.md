
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
<img width="2048" height="1236" alt="drawing" src="https://github.com/user-attachments/assets/89362d83-75d7-429a-9c16-776e13f7f2d2" />


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
We spend this day mainly focusing on getting the fall detection working using and ESP32-WROOM-S3 dev board and the aforementioned IMU. We had some ideas on how to implement fall detection but we ended up using a state machine approach. We had 4 states NORMAL → FREEFALL → IMPACT → FALLEN. Normal would be normal use around 10m/s^2 while Freefall would be when its less thatn 5 m/s^2 for 20 samples, we polled at 100hz, Impact would be when it was greater than 100 and fallen is when it was at rest. After falling a buzzer would go off. 
<img width="1500" height="1999" alt="img4" src="https://github.com/user-attachments/assets/b3e27032-06d4-4d3b-86ab-ddd5b3f3a14e" />

## *2026-03-28 BLE APP*
I started working on the andorid app today. I started with using our ESP32 dev board in order to get a BLE connection with the phone. I used an app that could detect BLE 4.2 and ble would work and connect to the andorid phone. Then I used android studio to try and start creating the app. I started with getting the navigation working, I decided to use the Google Map directions API and the places API in order to auto fill results that were near. I used the location on the phone in order to call the directions API and displayed the directions on the phone.

<img width="603" height="1306" alt="E7836057-D608-418E-8137-286C2339B75C_1_105_c" src="https://github.com/user-attachments/assets/039c3d1c-6c64-4651-82ea-8f5cd677c804" />

## *2026-04-01 Individual Progress Report and 2nd Breadboard Demo*
This week I submitted my indvidual progress report. I talked about the work I did on the BLE Andorid App as well as the fall detection I worked on with my group. For the breadboard demo Abdulrahman added the object detection as 2 coin montors to vibrate at different speeds based on how close the object was. Eraad also assembled the pcb togethet.

<img width="1206" height="1226" alt="image" src="https://github.com/user-attachments/assets/68b2e4fa-8ccf-44fc-8fd8-de9330f9eb0b" />

## *2026-04-07 2nd Progress Demo and V1 PCB Assembly*
Today I continuted working on the app getting live updates as you walk to update the directions. Basically when you got to the end of the direction that you were on, within 20 meters, the next direction would display and audiobly say it using tts. I also added a BLE screen were you can connect to the ESP32 cane and set an emergecny contact for fall detection. We also got a sim card for the phone and a simple phone plan. <img width="603" height="1306" alt="70163885-05B4-4A20-94C4-8062ED987675_1_105_c" src="https://github.com/user-attachments/assets/594327fd-d98a-42ff-b36e-d27c93a228c8" />


## *2026-04-15 Final PCB Assembly and Machine Shop*
The final PCB was assbemled and the Machine shop finished our box and cane attachment

<img width="1500" height="1999" alt="image" src="https://github.com/user-attachments/assets/9d1c8322-5fba-4d43-a845-488c5e1bbc64" />

We moved the stuff from the breadboard onto the PCB and retested everything with our actual cane attachement. We noticed that fall detection was kinda iffy so so we spent a lot of time working on the parameters on that. Everything else worked find and the app connected to the cane and all motors worked for haptic directions and we implemented sos using sms so when the cane fell if you didnt cancel the sms withtin 10 seconds it would send it to the contact you entered with the last known location. 

## *2026-04-21 Mock Demo and Work Left*
Most of the work is done for the Mock demo we are thinking about 3d printing buttons as well as adding language feature on the app that changes the lnaguage on the phone to whatever its set to.

## *2026-04-30 Final Demo and Final Presentation

Final demo and presentation went well we prepared very good slides and practiced. 
<img width="1999" height="1500" alt="image" src="https://github.com/user-attachments/assets/1f96e54c-ff77-475b-8461-3abc52921d4e" />







