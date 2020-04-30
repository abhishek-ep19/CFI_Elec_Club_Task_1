# CFI_Elec_Club_mini_task_1
  The 25 different projects to be submitted
### 1. Receiving Images From Passing Weather Satellites (NOAA and METEOR M2) Using a Cheap SDR
  First, we need radio antenna to receive the signal and an SDR (Software Defined Radio) attached to it. In SDR, the receiver would be connected to analog-to-digital converter. Then the digital signal-processor would read the converter & do the required processing, i.e. to filter or compress the data stream according to the needs. To build the antenna at least 10 feet of 50ohm coaxial cable, 8 pieces cut to 21 inches long wire & some other stuffs like wood, soldering iron, etc would be required.
<br />
&nbsp;
A double cross antenna is 4 dipole antennas mounted together (a dipole antenna being just 2 pieces of bare wire), one at each cardinal direction and tipped at an angle. This allows the antenna to be omnidirectional and receive signals regardless of where the satellite is in the sky. The dipoles are mounted at an angle to the axis of the pole(see next section) because the signal from the satellites is right hand circularly polarized.
<br />
&nbsp;
<p align="center">
  <img width="300" height="360" src="https://user-images.githubusercontent.com/64124723/80127386-e079b680-85b1-11ea-8af5-4d83fbbe719d.jpg">
  <br />Image of dipole connections in antenna (Wiring)
</p>
<br />
&nbsp;
To control SDR we need software like  SDRSharp (SDRSharp does not require installer). Since the satellites that we're interested in are in polar orbit (they orbit the earth around the poles) we can't listen for them whenever we want. Now, we have to receive signal from them only when the satellite is overhead. This means we now need a tracker to figure out where they are and for this 'Orbitron' program is used.
With the antenna made, we can now connect the output line to our SDR and plug the SDR into the usb port of a laptop.They'll all be at 137 Mhz but differ by several hundred Kilohertz.
In the SDR settings menu, set the type of radio to Wide band FM (WFM). The signals bandwidth is about 50 Khz but we'll have to set the SDR's bandwidth wider than that. As the satellite moves the signal is doppler shifted based on if the satellite is moving toward or away from us. In the Recording settings, uncheck Baseband, and select Audio.
<br />
&nbsp;
The audio that's recorded by SDRsharp is too fast for our decoding program, so we need to resample it at a lower speed. The easiest way to do that is with a program called Audacity, though there is a command line tool called Sox which also works for this.
In the bottom left corner there's drop down menu called Project Rate. Click it and select 11025. We'll be using a program called WXtoIMG to decode our recording. In the File menu click Load Audio & navigate to where you saves the resampled recording and select it. The program will automatically decode the file and produce an image when it's done.
<br />
&nbsp;
<p align="center">
  <img width="400" height="400" src="https://user-images.githubusercontent.com/64124723/80131939-9a742100-85b8-11ea-9840-534c403bc0d4.jpg">
  <br />Final Image Result
</p>
<br />
&nbsp;

### 2. Game That Learns How to Play Itself
  First, to make this project, the tools we need are Arduino Nano R3, MG-90s servos, MR105ZZ ball bearing, Microsoft Windows 10, Unity, 3D Printer and screwdriver, etc. For the game and machine learning part we use the game engine Unity coupled with the ML-agents toolkit also developed by Unity. The ML-agent tool kit comes with a few pre-built examples, one of them being a ball balancing exercise, that could easily be turned into a game requiring only a single joystick.
<br />
&nbsp;
<p align="center">
  <img width="450" height="360" src="https://user-images.githubusercontent.com/64124723/80213740-41a79580-8657-11ea-8ea5-67f03345a95a.jpg">
  <br />Ball Balancing exercise | Image from Unity ML-agent
</p>
<br />
&nbsp;
  Design a simple arm with the help of MG-90 motors and connect it to arduino nano R3 board that would actuate the joystick.The next step was to write a simple program for the Arduino that would allow it to control the joystick. A simple unity scene was then created to help roughly calibrate the joystick movements. AI looks for the speed and location of the ball and also the angle of the platform following its observations it will take an action (move the joystick).Depending on the outcome of this action, it will either receive a punishment if the ball falls (negative score) or a reward (positive score) if the ball remains on the platform, the closer the ball is to the target the bigger the reward is. The cycle then repeat itself until the AI learns how to take the decisions required to gain a maximum score. The best solution to this problem could be if the first half would happen without hardware. This means that we can train multiple AI at once and speed up time 20 folds as in real life, training one joystick directly for that would take much more hours & then afterwards, introduce the hardware in the second part of the training to make sure the AI would adapt to the hardware. Now, the hardware only requires time to train hardware, but gradually after sometime, the game would learn to play itself much better.
<br />
&nbsp;
<p align="center">
  <img width="450" height="360" src="https://user-images.githubusercontent.com/64124723/80218260-9569ad00-865e-11ea-9e61-0f2a311d0a9d.gif">
  <br /> Game learning to play itself
</p>
<br />

### 3. Electronic Stamp
Before starting with the project we need to know what actually happens in a normal inkjet. An inkjet printer cartridge these days is an advanced system, with perhaps hundreds of 'nozzles'. A nozzle is a small hole from which a droplet of ink is fired. The method of firing differs from manufacturer to manufacturer. In the case of the Hewlett Packard (HP) cartridge that we use in this circuit, the nozzles are operated thermally. In a normal inkjet printer the print head is moved back and forth with a motor and a guiding system. If however, we want to make a manageable device then it is not convenient to integrate this entire system into an electronic stamp.
<br />
&nbsp;
<p align="center">
  <img width="450" height="360" src="https://user-images.githubusercontent.com/64124723/80280597-a845b580-8722-11ea-9f7e-56e5568002b9.jpg">
  <br />Schematic Diagram of microcontroller with the cartridge
</p>
<br />
&nbsp;

<br />B1: 9V battery
<br />C1, C2: electrolithic capacitor, 22uF
<br />C3: capacitor, 100nF
<br />C4: capacitor, 22uF, 25V
<br />L1: See text
<br />IC1: 78L05
<br />IC2: ATTiny2313
<br />D1: 1N4001
<br />R1: trimpotmeter, 10K
<br />R2-R5: 4K7
<br />T1: STD12NF06, see text
<br />T2-T5: BC550
<br />T6-T9: BC560
This works as follows. The microcontroller attempts to keep the voltage at PD6 at 2.5V. It does this by making the pulses it generates on PD5 longer or shorter. These pulses cause T1 to conduct which results in a current through L1. When T1 blocks, that current continues to flow for a short time due to L1. C4 is now charged via D1. The current that flows into C4 allows the voltage across C4 to be higher than the power supply voltage. This voltage is divided via R1 and supplied to PD6. In this way the microcontroller regulates the voltage across C4 to a set value. R1 is used to adjust the voltage across C4 to the required 20V. Start with the potentiometer in the centre position and turn towards the ground connection to increase the voltage to 20V. The power supply for the microcontroller is handled by the 78L05 and the necessary decoupling capacitors around it.

In addition to the PWM logic that is programmed into the microcontroller, there is also a simple character generator built in. Even though it is possible to obtain quite a high resolution (32 nozzles are being controlled) the font uses just 8x8 pixels per character. This low resolution was deliberate because there is only 2k of flash ROM available in the microcontroller. By selecting a microcontroller with more ROM a better font could be used. A considerable amount of rummaging through the junkbox was involved for this project and unfortunately the author did not have a 'bigger' microcontroller on hand. The characters are generated based on a small sentence in the flash ROM. These are then sent to the nozzles. The sectors are made active one by one and when a sector is active only one nozzle is activated. The reason that this is done for each individual nozzle is that the print head would otherwise create a local vacuum for itself. This would result in (temporarily) no ink from the print head. By changing the nozzles, the nozzles that are not driven are given time to fill with ink again.
<br />There are a few aspect of the circuit that could be improved. Firstly, the nozzles that have been used are not spread evenly across the cartridge. It is however quite a lot of work to figure out exactly how to drive all the nozzles and the pins used here already produce a quite legible text. Secondly, the current consumption is not really suited to a little 9-V battery. With long texts this battery is temporarily exhausted quite quickly. It is of course possible to replace it with a 9-V NiCd or NiMH battery. These have no problems delivering short-duration current spikes. Thirdly, the text that the stamp produces is fixed, defined by the code in the microcontroller. With a little bit of work it can be changed to use the EEPROM instead and be made adjustable via, for example, a serial cable.
&nbsp;

### 4. Eco-friendly metal detector - Arduino
There are multiple variations of Metal Detector designs. This particular type of metal detector is a Pulse Induction detector which uses separate transmit and receive coils.
The Arduino produces a pulse which is applied to the Transmit Coil for a very short period of time (4uS) via a transistor. This current from the pulse causes a sudden magnetic field to form around the coil, the expanding and collapsing field induces a voltage into the Receive Coil. This received signal is amplified by the receiving transistor and then turned into a clean digital pulse by a Voltage Comparator and in turn sampled by a Digital Input pin on the Arduino. The Arduino is programmed to measure the pulse width of the received pulse.
In this design, the received pulse width is determined by the receive coil inductance and a capacitor. With no objects in range, the baseline pulse width measures approximately 5000 uS. When foreign metal objects come into range of the expanding and collapsing magnetic field this causes some of the energy to be induced into the object in the form of eddy currents ( Electromagnetic induction)
The net result is that the received pulse width is reduced, this difference in pulse width is measured by the Arduino and displayed on a TFT display in various formats.
<br />
&nbsp;
<p align="center">
  <img width="450" height="360" src="https://user-images.githubusercontent.com/64124723/80281770-17270c80-872b-11ea-9fd8-98e0a9af7f05.jpg">
  <br />Metal coils in metal detector
</p>
<br />
&nbsp;
<br />
&nbsp;
<p align="center">
  <img width="450" height="360" src="https://user-images.githubusercontent.com/64124723/80281960-5ace4600-872c-11ea-8b61-69b2553d23e6.jpg">
  <br />Metal Coil magnetic field induction(Eddy Current) effect
</p>
<br />
&nbsp;

The parts required are Arduino Mega 2560 (Items 1, 2 and 3 can be purchased as one bundled order), 
3.2" TFT LCD Touch Screen (Ive included code for 3 supported variations), 
TFT 3.2 Inch Mega Shield, 
Transistor BC548 x 8, 
0.047uf Greencap Capacitor x 4 (50v), 
0.1uf Greencap Capacitor x 1 (50v), 
1k Resistor x 4, 
47 Resistor x 4, 
10k Resistor x 4, 
1M Resistor x 4, 
2.2k Resistor x 4, 
SPST Mini Rocker Switch, 
Integrated Circuit LM339 Quad Differential Comparator, 
Signal Diodes IN4148 x 4, 
Copper WireSpool 0.3mm Diameter x 2, 
Two Core Screened Cable - 4.0mm Diameter - 5M length, 
USB Rechargeable Powerbank 4400mHa, 
Piezo Buzzer, 
Vero Board 80x100mm, 
Plastic Case minimum 100mm Height, 55mm Depth, 160mm Width, 
Cable Ties, 
MDF Wood 6-8mm Thickness - 23cm x 23cm square pieces x 2, 
Micro USB extension cable 10cm, 
USB-A plug cable suitable to be cut down to 10cm length, 
Headphone Audio Jack Point - Stereo, 
Various wood and plastic spacers detector head, 
Speed Mop Broom handle with adjustable joint (one axis movement only - see photos), 
One piece of A3 Paper, 
Glue Stick, 
Electic Jig Saw cutter, 
A4 Sheet Cardboard 3mm thickness for creating a coil former for TX and Rx coils, 
Duct Tape, 
Hot Glue Gun, 
Electric Glue, 
10 additional Arduino Header Pins, 
PCB Terminal Pins x 20, 
TwoPart Epoxy Glue - 5 min drying time, 
Craft Knife, 
5mm Plastic Tube length 30mm x 4 (I used garden watering system tubing from hardware store), 
MDF Waterproof sealer (Ensure does not contain metal) & 
60cm Flexible Electrical Conduit - Grey - 25mm Diameter. Make the connections and assemble the parts accordingly.
<br />
&nbsp;
<p align="center">
  <img width="450" height="360" src="https://user-images.githubusercontent.com/64124723/80282058-f2cc2f80-872c-11ea-9ec5-3fd333bd41ce.jpg">
  <br />Schematic diagram of connections
</p>
<br />
&nbsp;

### 5. Raspberry Pi micro arcade machine
We have to connect 2.4" LCD with an ILI9325 controller configurable to do 8-bit transfers and Raspberry Pi first. The 8-bit transfer mode was awesome, because it meant we could directly connect it to the GPIOs of the P1 header of the Raspberry Pi. That made the hardware really simple, and also much quicker because the data wouldn't have to be serialized first. The LCD has a 16-bit interface, which needs too many pins to connect it directly to the Raspberry Pi. To make it talk over just 8 of the 16 datalines, you need to move a jumper resistor from J1 to J2. We also need framebuffer module for intelligent displays to run LCD display installed in Raspberry Pi. Now, with the help of 3D printer the design of case for the game could be printed in whichever way we want the game to be. To interface the buttons and analog joystick to the Raspberry Pi, we we'll use M-Joy, which is a firmware one can burn into an ATMega8 to use it as an USB HID-based joystick. The problem with the Raspberry Pi is that it needs 5V and the Raspberry Pi isn't specced to run off any USB input voltage and can eat up more power than a USB port is specified to deliver.So, we have to build a battery powered 5V source. The LCD is controlled over 5 lines: 4 for the SPI-interface and one to reset the LCD. It also needs 3.3V for is power supply.
&nbsp;

### 6. Cell Phone Operated Land Rover
Traditionally, wireless controlled robots make use of RF (radio frequency) circuits, which have their disadvantages of restricted operational range, limited frequency range, and limited control. This project introduces the use of the mobile phone for robotic control.  This technology is more controller friendly as it doesn’t interfere with other controllers and can use up to twelve controls.  It also has the advantages of robust control and provides working range as large as the coverage area of the service provider. Although the look and capabilities of these robots vary, they share mechanically movable structures under some form of control. 
<br />The robot is controlled by making a call on the mobile phone attached to the robot. In the course of the call if any button is pressed a ‘dual-tone multiple-frequency’ (DTMF) tone is heard at the other end of the call. The cell phone mounted on the robot perceives this tone and then the robot processes it by the ATmega16 microcontroller with the help of DTMF decoder MT8870. The robots are controlled in three phases namely reception, processing, and action. Here preceptors are sensors mounted on the robot and the processing is done by on-board microcontroller or processor. This robot works either with the help of motors or with some other actuators.
&nbsp;

### 7. Handwriting Recognition
The hardware required for this project are SparkFun RedBoard Artemis ATP, SparkFun 9DoF IMU Breakout - ICM-20948 (Qwiic), SparkFun 9DoF IMU Breakout - ICM-20948 (Qwiic), SparkFun Qwiic Cable - 500mm, Grove - Mech Keycap, Seeed Grove - Mech Keycap, Gameduino 3. As its input, it takes multidimensional accelerometer and gyroscope sensor data. Its output will be a simple classification that notifies us if one of several classes of movements, in this case 0 to 9 digit, has recently occurred. To capture accelerometer and gyroscope data in a discrete real-time steps is a time consuming and error-prone task. So, we'll use Artemis ATP development board with a Gameduino 3 touchscreen (an Arduino shield) to present a user interface which allows to select numeral (0 to 9) and also the last readings can be deleted if there was some error while data capturing. A SparkFun 9DoF IMU Breakout - ICM-20948 (Qwiic) is used to capture the accelerometer and gyroscope data. The IMU Breakout is attached to a pen close to the tip and it is connected to the Artemis ATP using a long (50cm) Qwiic cable. Using the touchscreen to start and stop the capturing was a bit slow since the screen needs right amount of pressure to response. To circumvent this issue we'll use a mechanical switch which is very sensitive to the clicks and did the right job. The captured data is saved to the files on a micro SD card attached to the Gameduino 3. Each pen movement data was captured as a separate file. The file contains no header line, only the multiple lines of the comma separated accelerometer (3-axis) and gyroscope (3-axis) data in a format as accel_X, accel_Y, accel_Z, gyro_X, gyro_Y, gyroZ. A little over 100 samples for each digits (0-9) were captured. The collected data has been split into training (60%), validation (20%), and testing (20%) datasets. Since the data was collected from the IMU sensor using scaled (16 bit) and digital low pass filter (DLPF) setting and they are already within a specified range of the accelerometer and gyroscope readings so we can use the raw data as is for training and inferencing. Since the data was collected from the IMU sensor using scaled (16 bit) and digital low pass filter (DLPF) setting and they are already within a specified range of the accelerometer and gyroscope readings so we can use the raw data as is for training and inferencing. A convolutional neural network is one of the best options suited for recognizing patterns in images and time-series sequence data. The first few layers are 2D convolution neural networks with few other regularization layers. The last layer is a fully connected dense layer with softmax activation which outputs a probability of all 10 classes. The training of the model was done on an Intel NUC with Linux and an eGPU (NVIDIA GTX 1080Ti). The TensorFlow 2.1 with Keras API is used for model creation and training process.1 The Artemis ATP receives the samples continuously from the IMU sensor and outputs the highest probability class on the Gameduino 3 shield display. The improvements could be 1. The inferencing rate can be improved if 8-bit quantized model is used. 2. Right now there are some ops missing in the TensorFlow Lite Micro SDK which do not allow conversion of Conv 2D to a quantized version. 3. collecting the data while pen is not moving (at rest in different orientations) can reduce false positives.
<br />
&nbsp;
<p align="center">
  <img width="450" height="360" src="https://user-images.githubusercontent.com/64124723/80310543-e31a1d00-87f8-11ea-97c6-49d6b5e3321d.jpeg">
  <br />Schematic diagram of connections
</p>
<br />
&nbsp;

### 8. Speech Recognition at the Edge
The hardware parts required are NXP i.MX RT1010 EVK, OLED Display Module (128X64), Male/Female Jumper Wires, Male/Female Jumper Wires,Male Header 40 Position 1 Row (0.1") &	Male Header 40 Position 1 Row (0.1"). The software requirements are NXP MCUXpresso IDE, NXP MCUXpresso SDK & TensorFlow. In this project, an application is built around a model trained to recognize words left, right, up, and down. Install MCUExpresso IDE. We can create a new project from the Quickstart Panel > New Project which displays a wizard where we can choose IMXRT1010 as development board. Install TensorFlow Lite for Microcontrollers. The model we'll be using is trained with the TensorFlow Simple Audio Recognition script. The model was trained on a Linux desktop with eGPU (Nvidia 1080 Ti) with four words "up", "down", "left", "right". The model was trained on a Linux desktop with eGPU (Nvidia 1080 Ti) with four words "up", "down", "left", "right". Other words from the datasets were used as "unknown". The created model is converted to the TensorFlow Lite model and the converted model is transformed into a C array file for deploying with the inferencing code. The TensorFlow Lite Micro SDK is used to run inference on the device. A convolutional neural network is used for the model creation. The audio is captured using Synchronous Audio Interface (SAI) with enhanced Direct Memory Access (eDMA) controller. The process begins by generating a Fast Fourier transform (FFT) for a given time slice—in this case 30 ms of captured audio data. The TensorFlow Lite model doesn't take in raw audio sample data. Instead it works with spectrograms, which are two dimensional arrays that are made up of slices of frequency information, each taken from a different time window. The OLED display is connected to the i.MXRT1010 EVK over I2C. The predicted word is displayed at the OLED display. The project can be build and debug using the MCUExpresso IDE Quickstart Panel > Build and Quickstart Panel > Debug respectively. 
<br /> Scope for improvements are: The inferencing rate can be improved if 8-bit quantized model is used. Right now there are some ops missing in the TensorFlow Lite Micro SDK which do not allow conversion of Conv 2D to a quantized version. Currently sometimes it misses some words due to accent or noise in the audio data. The accuracy of the model can be improved if it is trained with more own voice data using transfer learning. Also, the on-board microphone data has some noise which can be either fixed using some settings or an external digital microphone can be used for better performance.
&nbsp;

### 9. Controlling a Motor with an H-Bridge
An H-Bridge can be used to control motors for robotic projects. An H-Bridge is an electric circuit that allows us to apply voltage to our motors in either direction allowing the motor to run forwards or backwards. The L293D is a dual H-Bridge motor driver IC which means that it is capable of driving two motors simultaneously. The following image shows the pin layout for the L293D IC. Since the output from the GPIO ports on the BeagleBone Black is usually not enough to drive our motors, the L293D has both a Vcc (3.3V from the BeagleBone Black) and a Vmotor (power for the motors 6V->12V). The L293D also has two enable pins which should remain high to enable the motors. If the enable pins are low the H-Bridge will be disabled.
<br />
&nbsp;
<p align="center">
  <img width="450" height="360" src="https://user-images.githubusercontent.com/64124723/80391568-89365780-88cb-11ea-8471-7748382b3820.jpg">
  <br />Schematic diagram of connections
</p>
<br />
&nbsp;
 Pins 15 and 25 of the P9 header are connected to the enable pins on the L293D IC. Both of these pins will need to be high to enable the motors. We have pins 11 and 13 of the P9 header connected to the IN1 and IN2 pins on the IC. We also have pins 21 and 23 of the P9 header connected to the IN3 and IN4 pins. The DC motors that we are driving with the L293D are connected to the OUT pins of the IC.
<br />Code written in terminal of beaglebone will be like:
<br />var leftMotor = try SBHBridge(forwardHeader: .P9, forwardPin: 11,
<br />                         reverseHeader: .P9,reversePin: 13,
<br />                        enableHeader: .P9,enablePin: 15,
<br />                         componentName:"Left Motor")
<br />var rightMotor = try SBHBridge(forwardHeader: .P9, forwardPin: 23,
<br />                         reverseHeader: .P9,reversePin: 25,
<br />                         enableHeader: .P9,enablePin: 27,
<br />                        componentName:"Left Motor")
<br />Now we can spin the motor in the forward direction like this:
<br />                        leftMotor.goForward()
<br />                        rightMotor.goForward()
And vice versa for other motor.

### 10. Internet Controlled LED Strip Using ESP32 + Arduino
The hardware required are	Espressif ESP32S, NeoPixel Ring: WS2812 5050 RGB LED,	Adafruit NeoPixel Ring: WS2812 5050 RGB LED & 5V DC power supply.
<br />ESP32 is running an HTTP server and each time you click a button the theme is changed. That HTTP server is accessible both through a local network and the internet.
<br />Connect 5V DC power supply to your LED strip. LED strip used in this tutorial contains 60 pixels and one meter, and needs even 3.5 A / m. Depending on how many pixels are you going to use buy an appropriate 5V DC power converted. LED strip contains only 3 input pins: +5V, GND and Din. ESP32 is powered from 3.3V that is obtained thanks to onboard LDO linear regulator. Connect your power supply to the LDO input pin - in my dev board it's called V5, but in your board it can be named differently. Connect LED strip data input pin Din to G12 pin on your board.
<br />Husarnet provides modified ESP32-IDF - thanks to that you can use almost the same API as in standard Arduino package for ESP32. Husarnet also provides easy integration with Arduino IDE.
<br />1. Install neopixelBus library in Arduino IDE
<br />2. Install Husarnet IDF for ESP32:
<br />3. Install ESP32 dev boards
<br />One can clone the code for ESP32 board or write by self.
<br />That's comfortable to add more than one network credentials here - in case of moving your project to different physical destinations you will not need to reprogram your ESP32 each time.
<br />// Add your networks credentials here
<br />const char* ssidTab[NUM_NETWORKS] = {
<br />  "wifi-network-1",
<br />};
<br />const char* passwordTab[NUM_NETWORKS] = {
<br />  "wifi-pass-1",
<br />};
<br />HusarnetServer server(8000);
<br />String header;
<br />void setup() {
<br />  Serial.begin(115200);
<br />  strip.Begin();
<br />  strip.Show();
<br /> And so on, to write code for the LED Strip. In Arduino IDE open Tools -> Serial Monitor and wait until your ESP32 is connected to Wi-Fi network. After a few seconds you should see a link. Copy that link and open it in your web browser. Open ledstripnet and left click ledstrip element
Select Make the Web UI public and click update button. In the Info column within ledstripnet network you should see Web UI button with a public available link to a control panel. Each time you will power your ESP32 board under that link you will have an access to a web UI to control your LED strip.
### 11. ESP32 Xiaomi Hack - Get Data Wirelessly
The hardware required are ESP32, a 2.8” color TFT display and the Xiaomi temperature and humidity sensor. Connect the TFT display with the ESP32 board as shown in the figure:
<br />
&nbsp;
<p align="center">
  <img width="450" height="360" src="https://user-images.githubusercontent.com/64124723/80408476-d8d54d00-88e4-11ea-854f-e77b1d8d733f.png">
  <br />Schematic diagram of connections
</p>
<br />
&nbsp;
The code for ESP32 board:
<br />#define SCAN_TIME  10 // seconds
<br />We initialize the display and the Bluetooth module of the ESP32 board and then we draw the user interface on the screen.
<br />
<br />void setup() {  WRITE_PERI_REG(RTC_CNTL_BROWN_OUT_REG, 0); //disable brownout detector
<br />  tft.begin();  Serial.begin(115200);
<br />  Serial.println("ESP32 XIAOMI DISPLAY");
<br />  initBluetooth();  drawUI();
<br />}
<br />Next, we search for Bluetooth devices nearby every 10 seconds. We don’t make a connection to the Xiaomi Device since it is not needed. We only scan for nearby Bluetooth low energy peripherals and check the broadcast advertisement packets. The humidity and temperature values are stored in those packets, so we only need to read them. After we read the values we display them on the screen. As always you can find a link to the code of this project in the description attached to this tutorial.
&nbsp;

### 12. ESP32 LoRa Sensor Monitoring with Web Server (Long Range Communication)
What to learn from this project:->
<br />Send sensor readings via LoRa radio between two ESP32 boards.
<br />Add LoRa and Wi-Fi capabilities simultaneously to your projects (LoRa + Web Server on the same ESP32 board)
<br />Use the TTGO LoRa32 SX1276 OLED board or similar development boards for IoT projects.
<br />The LoRa sender sends BME280 sensor readings via LoRa radio every 10 seconds;
<br />The LoRa receiver gets the readings and displays them on a web server;
<br />You can monitor the sensor readings by accessing the web server;
<br />The LoRa sender and the Lora receiver can be several hundred meters apart depending on their location.
<br />So, you can use this project to monitor sensor readings from your fields or greenhouses if they are a bit apart from your house;
<br />The LoRa receiver is running an asynchronous web server and the web page files are saved on the ESP32 filesystem (SPIFFS);
<br />The LoRa receiver also shows the date and time the last readings were received.
<br />To get date and time, we use the Network Time Protocol with the ESP32.
<br />
&nbsp;
<p align="center">
  <img width="400" height="450" src="https://user-images.githubusercontent.com/64124723/80447042-fb438680-8935-11ea-9f84-be6f3abeea3d.png">
  <br />Schematic diagram of connections
</p>
<br />
&nbsp;
<br />To program the TTGO LoRa32 SX1276 OLED boards we’ll use Arduino IDE. To upload files to the ESP32 filesystem, we’ll use the ESP32 filesystem uploader plugin. We need to install OLED, LoRa and BME280 libraries. We also need ESPAsyncWebServer and AsyncTSP libraries for building asynchronous web server. Everytime the LoRa receiver picks up a new a LoRa message, it will request the date and time from an NTP server so that we know when the last packet was received. We have to download NTPClient library.
<br />The BME280 we’re using communicates with the ESP32 using I2C communication protocol. Connect Vin to 3.3V, Gnd to Gnd, SCL(Serial Clock Pin) to GPIO 13 & SDA to GPIO 21.
<br />//define the pins used by the LoRa transceiver module
<br />#define SCK 5
<br />#define MISO 19
<br />#define MOSI 27
<br />#define SS 18
<br />#define RST 14
<br />#define DIO0 26
<br />//select LoRa frquency: #define BAND 433E6 //for Asia
<br />Define the OLED pins. Define the OLED size. Define the pins used by the BME280 sensor. Create an I2C instance for the BME280 sensor and a bme object. Create a display object for the OLED display. Get readings from BME sensor. Send readings via LoRa. Now, sensor readings are send every  seconds. The LoRa Receiver gets incoming LoRa packets and displays the received readings on an asynchronous web server. Create an index.html file, we can also include CSS and Javascript in the html code file. Now do the same for transciever module. The processor() function is what will attribute values to the placeholders we’ve created on the HTML file. It accepts as argument the placeholder and should return a String that will replace that placeholder. After inserting your network credentials, save your sketch. Then, in your Arduino IDE go to Sketch > Show Sketch Folder, and create a folder called data. Inside that folder, you should have the HTML file and the image file.
&nbsp;

### 13. Personal Assistant
The main components of this project are a Microcontroller and a Music Player module. Our microcontroller (NodeMCU) uses WiFi technology to connect to an access point with internet connection; so it can gets its required data, process it, and tells the Music Player (DFPlayer Mini) when, which MP3 file should be played. We will have the operations lined up in the operations queue. To know the no. of google unread messages we need to use Google Atom Feed that can also be used by RSS Readers. We send an HTTP request to access gmail feed and its response is in XML format. So, we count number of unread messages and use it in our program. Our file gets data from Yahoo Weather and simply sends it to us. Since we have Internet access, we will use a NTP Client to get time from a NTP Server. Libraries used are ArduinoJson, DFRobotDFPlayerMini & NTPClient. We use a micro SD card to store the MP3 file pieces. It's NodeMCU who decides which file should be played at what time and DFPlayer Mini helps him in making a meaningful sentence by decoding the MP3 files. To find the IP address for NodeMCU run Nmap on linux terminal.
&nbsp;

### 14. Video Card made on Breadboard
In this project we aim to display an image on monitors using EEPROM, counters etc. To display an image we need to have horizontal sync and vertical sync outputs and for that we are using 10 Mhz frequency generator, 3 counters each atteached to make 12 bit counter. In hsync, we need to have signal high for display+ front porch and then, low for sync pulse and then again high for Back porch. So, when these numbers of time are reached in counters we will have the signal high to let us know that the counters have reached the time. For hsync, we'll be using 200ns for display, 10 for front porch, 32 for sync pulse and 22 for back porch. Similarly, we will do it for vsync and display time as 600 ns. Now, we'll upload the image on EEPROM with adjusted figures of pixel according to connections in counters and the 64 colours we'll be having for display. Now, after executing we can get the image.

### 15. Raspberry Pi Radio
Install the OS Raspbian with desktop on the Pi.
Connect the Pi to your Wifi network and enable SSH and GPIO in Raspian settings. The input of the audio amplifier is connected to the audio output of the Pi. A capacitor is placed over the 5V of the Pi to decrease noise. The hardware is connected to as what is shown in the schematic diagram. The software consists of a Python script that is run automatically upon boot. Upload the file Radio1.py to /home/pi.
### 16. Gesture Controlled Universal Remote With Node-MCU
Node-MCU has only one input analog pin so we need multiplexer IC for atleast 5 flex inputs. The IC works by turning on one analog input, reading it, and turning it off. It then turns on the next analog input. By doing this, it only reads one sensor at a time, sending it to the microcontroller's analog pin. The IC is able to turn on, read, and turn off the analog inputs so quickly that it seems as though it is reading them all at the same time. For the glove to know the correct signal to send, signals must be received from your TV/appliances remote and programmed into the glove's code. To receive these signals, an IR receiver is necessary. Download IRremoteESP8266 library. Now some code arrangements are to be done to make it work with the TV Remote i.e. change the dataSet to powerOn etc. The possibilities for expandability are endless!
### 17. Arduino & Sony Ericsson: Gsm Shield Hack
The arduino GSM shield would allow to control arduino from anywhere in the world. However such a shield does unfortunately not come cheap. The arduino and the cellphone will need to communicate that's why we'll put the phone in PDU mode in the setup of the program.
To prepare the arduino board use the board type in tools as 256 Serial Buffer Arduino board which will give us 64 byte limit but we can increase the size of serial buffer. To increase its limit, create a complete copy of the arduino core code, modify the buffer size in the new core code and then to create a new board which is listed in the Arduino IDE which uses this new core directory. Now, connect Tx and Rx of arduino with pins 4 and 5 respectively. Also connect the ground to pin 10 and its optional to have power from phone for the arduino borad. Now we can get an online encoder for code of PDU. The encoder allows you to see how your number looks like in PDU (the numbers get mixed up) and how a message looks like in PDU. Upload the code and put your number there so that no one else can access that arduino borad.
### 18. ATtiny85 Mini Arcade: Snake
Since it is a mini game we'll be using the ATtiny85 and simple 2 axis joystick & DFRobot’s 128 x 64 OLED screen.Make the connections. Now, we'll add specifications to the game like the snake eating the fruit and fruit getting added at a random new location.
### 19. ESP32 + MPU9250: 3D Orientation Visualisation
MPU9250 is IMU (Inertial Measurement Unit) combines not only 3D accelerometer, 3D gyro and 3D compass but also DMP (Digital Motion Processor). A web page with a 3D cube visualizing orientation of MPU9250 is hosted by ESP32. Real time data from MPU9250 is sent to a web browser through a websocket. Data is visualised by the three.js library to visualise the orientation of the cube. Connect P22 to SCL, P21 to SDA, P19 to INT & GND to GND. Install husranet and ArduinoJson library in arduino IDE. Install arduinoWebsockets-master so that data can be sent back and forth. Install SparkFun_MPU-9250-DMP_Arduino_Library also to have the data from IMU sensor and process it. Upload the program on the ESP32 and go to the web page hosted by the ESP32 after getting the http link.
### 20. Arduino Cell Phone 4G Signal Booster / Repeater
The cell phone base station signals are constantly being transmitted from one or more masts owned by the phone company. The external antenna receives the good quality signal and sends it down a shielded cable to a filter which very accurately stops everything except a very small slice of frequencies. For phone, these frequencies are centered around 806 MHz and have a spread, or bandwidth, of 30 MHz. The signal then goes into a LNA (Low Noise Amplifier) which does a fair bit of amplification at low power. It's much more efficient to 'cascade' the amplifiers rather than try and do everything with one device. Next is the Variable Gain Amplifier, or VGA, which does most of the grunt work and has the ability to be controlled by a microprocessor by means of very simple SPI code.
 The gain needs to be controlled as sometimes the base station signal can be quite strong and we don't want to damage our phone or create a feedback loop between the two antennae. Simultaneously, the signal comes out of the BPF and routes into an RSSI (Received Signal Strength Indicator) which provides an analogue signal ie a DC voltage to the micro controller, which can turn down the VGA if the signal is too strong. At the moment, control of the VGA is manual by means of a slide potentiometer. Get the band pass filters and low noise amplifier module. Connect VGA to the arduino board by connecting pins for clock, Chip select and MOSI. Connect the TFT screen to the arduino board. Upload the code in the arduino board.
### 21. 






