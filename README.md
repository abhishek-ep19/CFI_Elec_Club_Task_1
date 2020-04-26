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
&nsbp;

### 7. Handwriting Recognition
The hardware required for this project are SparkFun RedBoard Artemis ATP, SparkFun 9DoF IMU Breakout - ICM-20948 (Qwiic), SparkFun 9DoF IMU Breakout - ICM-20948 (Qwiic), SparkFun Qwiic Cable - 500mm, Grove - Mech Keycap, Seeed Grove - Mech Keycap, Gameduino 3. As its input, it takes multidimensional accelerometer and gyroscope sensor data. Its output will be a simple classification that notifies us if one of several classes of movements, in this case 0 to 9 digit, has recently occurred. To capture accelerometer and gyroscope data in a discrete real-time steps is a time consuming and error-prone task. So, we'll use Artemis ATP development board with a Gameduino 3 touchscreen (an Arduino shield) to present a user interface which allows to select numeral (0 to 9) and also the last readings can be deleted if there was some error while data capturing. A SparkFun 9DoF IMU Breakout - ICM-20948 (Qwiic) is used to capture the accelerometer and gyroscope data. The IMU Breakout is attached to a pen close to the tip and it is connected to the Artemis ATP using a long (50cm) Qwiic cable. Using the touchscreen to start and stop the capturing was a bit slow since the screen needs right amount of pressure to response. To circumvent this issue we'll use a mechanical switch which is very sensitive to the clicks and did the right job. The captured data is saved to the files on a micro SD card attached to the Gameduino 3. Each pen movement data was captured as a separate file. The file contains no header line, only the multiple lines of the comma separated accelerometer (3-axis) and gyroscope (3-axis) data in a format as accel_X, accel_Y, accel_Z, gyro_X, gyro_Y, gyroZ. A little over 100 samples for each digits (0-9) were captured. The collected data has been split into training (60%), validation (20%), and testing (20%) datasets. Since the data was collected from the IMU sensor using scaled (16 bit) and digital low pass filter (DLPF) setting and they are already within a specified range of the accelerometer and gyroscope readings so we can use the raw data as is for training and inferencing. Since the data was collected from the IMU sensor using scaled (16 bit) and digital low pass filter (DLPF) setting and they are already within a specified range of the accelerometer and gyroscope readings so we can use the raw data as is for training and inferencing. A convolutional neural network is one of the best options suited for recognizing patterns in images and time-series sequence data. The first few layers are 2D convolution neural networks with few other regularization layers. The last layer is a fully connected dense layer with softmax activation which outputs a probability of all 10 classes. The training of the model was done on an Intel NUC with Linux and an eGPU (NVIDIA GTX 1080Ti). The TensorFlow 2.1 with Keras API is used for model creation and training process.1 The Artemis ATP receives the samples continuously from the IMU sensor and outputs the highest probability class on the Gameduino 3 shield display. The improvements could be 1. The inferencing rate can be improved if 8-bit quantized model is used. 2. Right now there are some ops missing in the TensorFlow Lite Micro SDK which do not allow conversion of Conv 2D to a quantized version. 3. collecting the data while pen is not moving (at rest in different orientations) can reduce false positives.
<br />
&nbsp;
<p align="center">
  <img width="450" height="360" src="">
  <br />Metal Coil magnetic field induction(Eddy Current) effect
</p>
<br />
&nbsp;

### 8. 


















