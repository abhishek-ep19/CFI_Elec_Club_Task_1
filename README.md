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
<p align="center">
  <img width="400" height="400" src="https://user-images.githubusercontent.com/64124723/80131939-9a742100-85b8-11ea-9840-534c403bc0d4.jpg">
  <br />Final Image Result
</p>




