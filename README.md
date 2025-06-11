# ConMon
sensor-works

Windows 10/11 OS

Download Requirements
You will need:
1. TwinCAT XAE (Please don’t download 4026, it operates on a package management
system and I don’t think the HMI has been released for it yet).
Download 4024.6*
https://www.beckhoff.com/en-gb/products/automation/twincat/texxxx-twincat-3-
engineering/te1000.html?
You can find the software in Product Information -> Documentation and downloads.
3. TF2000 – This is the HMI server, you can install this on your development PC
https://www.beckhoff.com/en-gb/products/automation/twincat/tfxxxx-twincat-3-
functions/tf2xxx-hmi/tf2000.html
4. TF3300 – Scope server
https://www.beckhoff.com/en-gb/products/automation/twincat/tfxxxx-twincat-3-
functions/tf3xxx-measurement/tf3300.html
5. TF3600 – Condition Monitoring, again don’t download the build for 4026
https://www.beckhoff.com/en-gb/products/automation/twincat/tfxxxx-twincat-3-
functions/tf3xxx-measurement/tf3600.html?
6. TE2000 - This is HMI Engineering, without this, the PLC and HMI project can't be compatable.


The training materials are https://github.com/QinSensor/twincat_training

How to Run:
1. Open TwinCAT XAE Shell in Windows OS;
File -> Open  -> Project/Solution, choose ConMon_UsingSensorWorks_and_Sim

2. Ensure gateway and sensors are power on, and then Set parameters:
    In solutions explorer on the left bar, open file: PLC -> GVLs -> GLOBAL,
   2.1  IP adress of your gateway:
   find line:
    strIPAddress : STRING := '192.168.4.44';
   replace with your own gateway's IP
   2.2 DeviceID of sensors:
   fine line:
   	strDeviceID  : ARRAY[1..GVL_Const.cMaxVibrationDevices] OF STRING := ['e0:f6:fd:c4:e3:08', 'd5:d0:f9:30:83:d7'];
   replace with your own sensors's device IDs.

   2.3 deviceID index:
   Open file:  PLC -> MAIN(PRG)
   in the lower part, find line:
       iRequestDeviceIndex := 1,                                      // Index of the device to talk to (1 or 2)
   replace 1 with the index you would like to get.

3. Build your project
   In Top menu, Build -> Build Solution
4. Activate Configuration
   In Top menu, TwinCAT -> Activate Configuration
   Press OK, and OK for following pop-ups.
5. Login and Start
   
   In Top menu, PLC -> Login
   Press PLC-> Start
   Now the project is running.
6. Check content fetched:
   
   In Solution Explorer(left block), Open file:  PLC -> POUs -> HTTP -> FB_RequestToGateway(FB),
   sContent stores what we fetched from gateway.



