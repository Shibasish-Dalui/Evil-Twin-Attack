# Evil-Twin-Attack

## Introducion

An Evil Twin Attack is a type of wireless attack where a malicious actor creates a 
fake wireless access point (AP) that masquerades as a legitimate one. The goal of 
this attack is to trick users into connecting to the malicious AP instead of the 
legitimate one, allowing the attacker to intercept data or perform other malicious 
activities. This type of attack may be used to steal the passwords of unsuspecting 
users, either by monitoring their connections or by phishing, which involves setting 
up a fraudulent web site and luring people there.

<img style="border-radius:10px;"
    src="https://github.com/Shibasish-Dalui/Evil-Twin-Attack/blob/main/evil_twin_attack.png">
<br>


## Requiremnts
➢ NodeMCU ESP8266 micro-controller ( x 2 ) <br>
➢ Power source <br>
➢ 7805 IC (if higher voltage source is used) <br>
➢ Micro-USB cable <br>
➢ Arduino IDE ( or any other supported code editor ) <br>
➢ NodeMCU Flasher <br>
➢ A general-purpose computer (ex. Laptop, phone , etc.) with Wi-fi support <br>


## Setup

### De-auther

Flash the [de-auther](https://github.com/Shibasish-Dalui/Evil-Twin-Attack/blob/main/esp8266_deauther_2.6.1_DSTIKE_USB_DEAUTHER_V2.bin) program in one of the ESP8266 micro-controller 
using NodeMCU Flasher software (or any other supported flasher). In this case, I am using this [Flasher](https://github.com/nodemcu/nodemcu-flasher).

### Rouge Access Point (Evil Twin)

1. In Arduino go to `File` -> `Preferences` add this URL to `Additional Boards Manager URLs` ->
   `https://raw.githubusercontent.com/SpacehuhnTech/arduino/main/package_spacehuhn_index.json`.
2. Download and open [EvilTwin.ino](https://github.com/Shibasish-Dalui/Evil-Twin-Attack/blob/main/EvilTwin.ino) with Arduino IDE.
3. Select an `ESP8266 Deauther` board in Arduino.
4. Connect the other ESP8266 micro-controller and select the serial port in Arduino under `tools` -> `port`.
5. Click Upload button.


## Execution
• Connect the micro-controllers to the power source . <br>
• Connect to the <b><i>pwned</i></b> Wi-Fi network. The password is <b><i>deauther</i></b>. <br>
• Open [](http://192.168.4.1/) on your browser. Select the network you want to attack. Then go to the <b>Attack</b> tab , click on <b>START</b> in the Deauth row. <br>
• Now connect to the <b><i>WiPhi</i></b> Wi-Fi network. The password is <b><i>DevilTwin</i></b>. <br>
• Again open [](http://192.168.4.1/) on your browser. Select the attacked network and click on <b>Start EvilTwin</b>. <br>
• Now we can notice that a network of same name appears (see without protection). Connect to it now. <br>
• By clicking on that network we get redirected to a webpage looking like a network portal. Putting a random password on the assumption that it might be a suspicious page.
  On clicking on Continue, we see that a dialogue about verification of given password is in process. If the password provided is not the actual password of the attacked network, then 
  it will show an error, again redirecting to the portal page, convincing the user that the portal page is genuine. <br>
• The process will keep on repeating unless the user provides the correct password of the attacked network. After the correct password is given and verification is done,
  the fake Wi-Fi will get vanished. The WiPhi Wi-Fi network will come back. On clicking that network we will get redirected to the EvilTwin webpage. 
  But, this time we can see that the password of the attacked network gets displayed also. Actually, what happened is that when the user’s password got verified, in 
  the backend, the password was sent to the EvilTwin webserver created by us (in the code). <br>


## Limitation

The <b>ESP8266</b> is only able to work on the <b>2.4 GHz</b> spectrum. There is no way to make it work on <b>5 GHz</b> unless a powerful alternative is used.
So make sure your target device is connected through <b>2.4 GHz</b>. Otherwise, the attack will simply not work.
