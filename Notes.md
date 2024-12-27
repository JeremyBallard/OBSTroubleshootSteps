# OBS Troubleshooting Notes
[Quick Start Guide via OBS Official Site](https://obsproject.com/kb/quick-start-guide)  
[Default Place to Check for initial troubleshooting help via OBS Official Site](https://obsproject.com/kb/category/2)

## Dropping Frames 
### User Experiencing issues related to Recording and Streaming
12/24/24 Version 30.2.3 on Windows 10  
User says "[stream] just goes good then for 2 seconds it like stops and starts i dont know how to explain, its just a basic lag..."  
User posts [log file](https://obsproject.com/logs/5lXOpH3kILrSQWA8), with 30 seconds of stream test to show a significant portion of frames dropping.  
![image](https://github.com/user-attachments/assets/08bd2e46-805f-49ae-9f9d-79a2f583709b)  

In the same log, recording starts and stops just before stream starts and stops.
![image](https://github.com/user-attachments/assets/cbe82504-d79e-4656-8047-dca3c8bfb28c)  
  
Assisting User (AU1) thinks there could also be a problem with capturing Minecraft in Game Capture, as detailed by this scene data  
![image](https://github.com/user-attachments/assets/dbdd4208-8a03-4c50-a7ce-48d80f85578e)

and this executable being captured by OBS.  
![image](https://github.com/user-attachments/assets/220e9a02-f331-4460-94f6-dfe9d5e7fd65)

AU1 directs user to [Minecraft: Java Edition Troubleshooting Guide](https://obsproject.com/kb/minecraft-java-edition-troubleshooting), unknown if user employs this guide.  
  
A [second log file](https://obsproject.com/logs/gY2JCmuo0h23tXCm) is dropped, and user is questioned by AU1 if user wants to stream and record at the same time. Recording starts and stops just before the same Streaming event.
  
Another Assisting User (AU2) notices that user's recording not locally, but rather to a OneDrive folder. This is also reflected in the first log. Possibly causing internet issues by continuously uploading twice,
once for stream and once for the local file recording.  
![image](https://github.com/user-attachments/assets/60de516b-ada6-42d8-bf4a-93f0c83933fb) ![image](https://github.com/user-attachments/assets/7ac3e41f-6f3e-4402-b10c-8688e0bd113b)

User is directed to change file path downloads by AU1, by going to Settings > Output and finding 'Recording Path' under the 'Recording' tab.  
![image](https://github.com/user-attachments/assets/29b42d0b-9541-425f-96e8-506fdc8bc490)

User uploads [3rd log](https://obsproject.com/logs/uFwZHdSoviOqMwVO), with changes to local recording path. Frame drops still detected but Assisting User 3 (AU3) correctly asks if OBS had been restarted since implementing all changes.

User restarts, does a test stream, and sends [this log](https://obsproject.com/logs/OpBiBNrPvOc58QIH), showing little frame drops.  
![image](https://github.com/user-attachments/assets/e50ed375-4d19-4563-95df-d732bd3dd8ae)

