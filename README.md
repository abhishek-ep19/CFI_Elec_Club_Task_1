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

### 3. Build an OctaPi - Raspberry Pi Supercomputer/Cluster
  Things we'll need are 9 x Raspberry Pi 3, 8 x Unicorn HAT (optional), 8 x short Micro USB cables, Wireless router, Power hub & Ethernet cable as hardwares and the software requirements are Python 3 dispy, Python 3 nmap, Python 3 psutil & Python 3 unicornhat. Now, we need a dedicated wireless router (local WiFi network) and it need not be connected to the internet. Connect a computer to the router using an Ethernet cable. Change IP address to 192.168.1.1. DHCP is a protocol used for issuing IP addresses automatically. we will make sure DHCP is enabled and set the DHCP address range to something that provides a useful range of addresses; we chose 192.168.1.2 to 192.168.1.254. To set up OctaPi client one of the Raspberry Pi will be used and on micro SD card latest version of Raspbian by following the software guide instructions will be installed. Using this micro SD card, boot up the Raspberry Pi 3 with a keyboard, screen, and mouse connected. And also ensure that Raspberry Pi 3 is connected to the internet. Install dispy: Distributed and Parallel Computing with/for Python & numpy by using commands 'sudo pip3 install dispy' and 'sudo apt-get install nmap'. Dispy is a distributed Python implementation that will allow you to write code on the client and run it across the servers. Nmap is used to discover the IP addresses of the Raspberry Pi servers forming the OctaPi cluster, so that they can be shut down or rebooted as needed. Then we need to download the OctaPi client software using command 'git clone https://github.com/raspberrypilearning/octapi-setup.git' and move files from client folder to home/pi by using command 'mv /home/pi/octapi-setup/client/* /home/pi'. Each of the Raspberry Pi 3 computers in the cluster needs to have its own micro SD card prepared. However, as each card is identical, you can set up just one server, check it’s working, and then replicate the SD card for the other servers.




























