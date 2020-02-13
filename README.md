# ESPNow-HelloWorld
This program is a simple ESPNow "hello World!" for  the ESP8266. </br>
It based on two on [ESP8266 – Witty Cloud Moduls](https://www.aliexpress.com/item/32597876082.html?scm=1007.22893.149155.0&pvid=b8c0fb1b-281a-4ba6-85a1-98dd68a536b9&onelink_page_from=ITEM_DETAIL&onelink_item_to=32597876082&onelink_publisherid=138687224&onelink_memberseq=0&onelink_duration=0.981192&onelink_status=noneresult&onelink_item_from=32597876082&onelink_subid=NULL&onelink_page_to=ITEM_DETAIL&aff_request_id=9ba6214ea2664d8d8daf087a377c6ab1-1580813465648-05603-mIyvFaQvV&aff_platform=product&cpt=1580813465648&sk=mIyvFaQvV&aff_trace_key=9ba6214ea2664d8d8daf087a377c6ab1-1580813465648-05603-mIyvFaQvV&terminal_id=cba704aee29744eba36caa98b7347143) and ESP-Now for the connection of both.

___

### Table of Contents

   1. [Installing Instructions](README.md#installing-instructions)
   2. [Projects based on this](README.md#projects-based-on-this)
   3. [Creater](README.md#creater)
  
___

### Installing Guide

Estimated time: ~ 20 minutes

1. Download the [Arduino IDE](https://www.arduino.cc/en/main/software) and install it. ([Install Guide](https://www.arduino.cc/en/Guide/HomePage))

2. Add the needed libraries. (`ESPNow-HelloWorld/Installation/..`) 

   - ESP8266 ([How to add libraries](https://randomnerdtutorials.com/how-to-install-esp8266-board-arduino-ide/))
   - Color   &nbsp; &nbsp; &nbsp;([How to add .zip - libraries](https://www.arduino.cc/en/Guide/Libraries))  (The library is in the installation directory)
   
3. Connect the ESP8266 that will be the server host to your PC.

   - Make sure your tool settings are correct (Port could be different)
   
   ![Settings in Tools](../docs/Settings%20for%20Tools.png)

4. Open the [GetServerMac](../Installation/GetServerMac) program in the IDE

5. Upload the program to the ESP. (`Ctrl + U`)

6. Open the serial monitor. (`Ctrl + Shift + M` or `Tools -> Serial Monitor` )

7. Copy the AP MAC and the STA MAC from the console to the [Server-Mac.txt](../Installation/Server-Mac.txt) file. <br/>
   *(There should be enough time, but if you have not received a printout on the monitor, press the reset button on the ESP)*

   ```
   Console Output Example:
   ===========================================================
   Gameserver
   -----------------------------------------------------------
   This node AP mac:  AF:FA:BC:02:E6:CD
   This node STA mac: AC:FA:BC:02:E6:CD
   ===========================================================
   ```
   
  8. Open the [LGGameserver](../Game/LGGameserver/LGGameserver.ino) program with the Arduino IDE.
  
  9. Upload the program to the ESP. (`Ctrl + U`)
  
 10. Open the [LGTarget](../Game/LGTarget/LGTarget.ino) program with the Arduino IDE.
 
 11. Change the server Mac addresses for the targets in the code (**_don't_** just copy the entire mac.txt file) `(Code row : 67 - 68)`
 ```
  
       // server esp mac addresses for the targets
       #ifdef TARGET

       uint8_t GAMESERVER_ap_mac[]   = {0xEE, 0xFA, 0xBC, 0x0C, 0xE6, 0xAF}; 
       uint8_t GAMESERVER_sta_mac[]  = {0xEC, 0xFA, 0xBC, 0x0C, 0xE6, 0xAF};

       // init sensor val
       int initVal;

       #endif
```
    
 12. Connect an ESP8266 that will be one of the targets.
 
 13. Upload the program to the ESP. (`Ctrl + U`)
 
 14. Repeat the steps <12> and <13> for every target.
 
 15. Software installation completed.
