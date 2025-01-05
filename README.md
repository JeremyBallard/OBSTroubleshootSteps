# OBS Troubleshooting Notes
[Quick Start Guide via OBS Official Site](https://obsproject.com/kb/quick-start-guide)  
[Default Guides to Check for initial troubleshooting help via OBS Official Site](https://obsproject.com/kb/category/2)

## Dropping Frames 
### User Experiencing issues related to Recording and Streaming
12/24/24 Version 30.2.3 on Windows 10  
User says "[stream] just goes good then for 2 seconds it like stops and starts i dont know how to explain, its just a basic lag..."  
User posts [log file](https://obsproject.com/logs/5lXOpH3kILrSQWA8), with 30 seconds of stream test to show a significant portion of frames dropping.  
![image](https://github.com/JeremyBallard/OBSTroubleshootSteps/blob/main/Images/RecordStreamFrameDrop.png)

In the same log, recording starts and stops just before stream starts and stops.  
![image](https://github.com/JeremyBallard/OBSTroubleshootSteps/blob/main/Images/RecordStreamStartStop.png)  
  
Assisting User (AU1) thinks there could also be a problem with capturing Minecraft in Game Capture, as detailed by this scene data  
![image](https://github.com/JeremyBallard/OBSTroubleshootSteps/blob/main/Images/RecordStreamSceneData.png)

and this executable being captured by OBS.  
![image](https://github.com/JeremyBallard/OBSTroubleshootSteps/blob/main/Images/RecordStreamGameHook.png)

AU1 directs user to [Minecraft: Java Edition Troubleshooting Guide](https://obsproject.com/kb/minecraft-java-edition-troubleshooting), unknown if user employs this guide.  
  
A [second log file](https://obsproject.com/logs/gY2JCmuo0h23tXCm) is dropped, and user is questioned by AU1 if user wants to stream and record at the same time. Recording starts and stops just before the same Streaming event.
  
Another Assisting User (AU2) notices that user's recording not locally, but rather to a OneDrive folder. This is also reflected in the first log. Possibly causing internet issues by continuously uploading twice,
once for stream and once for the local file recording.  
![image](https://github.com/JeremyBallard/OBSTroubleshootSteps/blob/main/Images/RecordStreamRecordingPath1.png) ![image](https://github.com/JeremyBallard/OBSTroubleshootSteps/blob/main/Images/RecordStreamRecordingPath2.png)
User is directed to change file path downloads by AU1, by going to Settings > Output and finding 'Recording Path' under the 'Recording' tab.  
![image](https://github.com/JeremyBallard/OBSTroubleshootSteps/blob/main/Images/RecordingPathChangeOBS.png)

User uploads [3rd log](https://obsproject.com/logs/uFwZHdSoviOqMwVO), with changes to local recording path. Frame drops still detected but Assisting User 3 (AU3) correctly asks if OBS had been restarted since implementing all changes.

User restarts, does a test stream, and sends [this log](https://obsproject.com/logs/OpBiBNrPvOc58QIH), showing little frame drops.  
![image](https://github.com/JeremyBallard/OBSTroubleshootSteps/blob/main/Images/RecordStreamPostSolutionFrames.png)

## Visual Issues  
### User Having Issues With Consistent Exposure on Logitech Camera  
12/26/24 User is on Windows 10, OBS 30.2.3, using a Logitech Camera  
![image](https://github.com/user-attachments/assets/8dde405f-a31d-4a8f-9b07-350386599976)

User posted following message (edited for conciseness): "hello everyone im having trouble with auto exposure... ive used my logitech g hub to make my camera a persistent profile... yet still outta know where [nowhere] the camera intesif[ie]s the [exposure] making way way way to[o] bright".  

User also posted sample comparison for what color profile should be    
![image](https://github.com/user-attachments/assets/af5b22e1-f490-4a5b-97ad-fd2f34b8bc45)  
and what camera randomly does.  
![image](https://github.com/user-attachments/assets/1fbc4216-7d6c-4485-ba37-b07ca45ba7f4)  

User also posted a [log](https://obsproject.com/logs/MC5NpiO14XL2MzA3), but log did not provide sufficient info for what is happening to the camera.  

I suggested user right click on the camera source,  
![image](https://github.com/user-attachments/assets/c07cc99b-2178-41a3-ad45-c87d0a513f2b)  
  
go to properties > configure video  
![image](https://github.com/user-attachments/assets/77d4e2d5-e8df-4ce7-a210-76766002ef0c)  

to pull up this screen.  
![image](https://github.com/user-attachments/assets/1566ed8c-f9af-428a-aaf1-79f90c04e01c)  

There is a Camera Control tab in settings. This is what user shows when screenshotting to that tab:  
![image](https://github.com/user-attachments/assets/341f55a2-aaeb-4fca-863f-a90a476db222)    

User had "Low Light Compensation" on, a Logitech setting that I have personally experienced the exposure being too high when on and it automatically adjusting while in OBS.  
  
This is the tooltip for what "Low Light Compensation" is doing. To me, this reads as "dynamically vary the **shutter speed**", or said more verbosely, the exposure is changed by dynamically dropping the speed since that allows more light in. I am unsure if this is what is happening but it's my best guess.  
![image](https://github.com/user-attachments/assets/23a09b43-668e-4a7e-acb9-3a064e4cf6b0)  
  
I suggested, for testing purposes, to have user turn off this setting in OBS. I also said to user that "it'll mess with white balance at first (Edit: not white balance, but exposure), you might have to recalibrate [your camera profile]".  

User turned off setting and is not happy with how dark camera frame is now. User turned G Hub profile back on, which turned on "Low Light Compensation" automatically in OBS.  

User posts this photo of G Hub settings:  
![image](https://github.com/user-attachments/assets/70185040-1948-4939-8616-601f22b27057)  

"Auto Exposure" is off, which unfortunately hides the setting for "Low Light Compensation" in G Hub.  
![GHubLL1](https://github.com/user-attachments/assets/f3dbd0a7-067c-47d8-ba93-4b2b45ce3ca9)  

I suggested to turn "Auto Exposure" on in G Hub, to turn "Low Light Compensation" off, and then turn "Auto Exposure" back off. Then, set the shutter speed and ISO to the desired exposure.  

This should adjust OBS's settings to match the preferred settings in G Hub. Unfortunately, it is unknown if computer restarts has an effect on these settings. I have not tested if "Low Light Compensation" turns back on after restart, but I have experienced issues with persistence on these settings, even with G Hub overwriting OBS's settings.  

User reported that "Low Light Compensation" being off had not caused any shift in exposure while passively testing in OBS. 
