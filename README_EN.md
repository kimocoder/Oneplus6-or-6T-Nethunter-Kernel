<div align=center><img src=images/LOGO.png width=100% ></div>


#Foreword

Whatsup guys , this is a trash noob rookie geek(ID:DJY) from China , today I want to share my project to you guys within my truly heart and hope you will enjoy it. Nethunter Kernel is an oneplus 6 and 6T full function¡¯s patch kernel, support hackrf, RTL-SDR , mouse jack, osmcombb+C118+openbts(these are basically hardwares) , Bluetooth attack , external infrared module , external OTG cable run pppoe router password sniff , OTG external multiple wireless network cables RTX series, MT7601 series, ahk9 series and htc series). Proxmark3 CDC HID diver support, chameleon-Mini diver support. This project is totally open source , no need to pay for it, please notice becasue there are some bitches selling it now(xxeyes team), and also check the MD5 value and hash value. For compile and debug this kernel I¡¯ve brush the device for hundreds of times , to solve the problems such as: flash kernel can¡¯t be open , can¡¯t use abd shell , can not external USB sevices, black screen , stuck at first screen and so on. It¡¯s been a long time for test and if there is still having bug, welcome to report. If you think this is useful please please please give me a *** STAR***  , your support is my
best motivation . ^ _ ^

And I will add some ¡®special words¡¯ to some losers , I don¡¯t owe you anything, or you can just choose to don¡¯t use it, but don¡¯t be like a dickhead that attack me. This is open source , I free share it , but all you did are not even say thank to me and just make some nonsense shit around, some fuckers even made my  thousand people group(2 groups!) that banned , what can you get from these? I wanna say more but I don¡¯t want to waste my fucking time to these piece of shit, so FUCK YOU

****
other languages: [Chinese](README.md)

# table of Contents
* [Install](#Install)
* [Update History](#Update History)
* [kernel picture and video demo DJY11-13](#kernel picture and video demo DJY11-13)
* [DJY15](#DJY15+)
* [DJY17-DJY19](#DJY17-DJY19)
* [Related test video collection](# Related test video collection)
* [FAQ](#FAQ)
* [file md5 and hash](#file md5 and hash)
* [Related code and module thanks list](#Related code and module thanks list)
* [Contact Information](#Contact Information)
#Install

1.You have to go to https://twrp.me/ download the twrp that relate to your device, and go to https://www.oneplus.com/support/softwareupgrade/ to choose your device download system(notice: the user in China have to get cross the firewall to download oos, why we don¡¯t suggest the One Plus¡¯s HOS system? Because HOS system in China are being limited on some permission functions, so there will be some commands or the terminal that can¡¯t be normal use , but it still works, but it won¡¯t be perfect, so there will be more prefer on oos)

2.Use my uploaded payload_dumper win or linux unpack the payload.bin firmware, then brush into twrp, mount all partitions, clean up the userdate partition, then clean up select all partitions and use my upload flash.sh or bat to brush In all the mirrors. This is the new OOS. ^ _ ^

3.After brush the TWRP , rebrush it(yes you have to brush it for twice), then choose adb sideload to push my DJY Nethunter Kernel.
```
adb sideload DJY XXX.ZIP
```
4.Then restart to the system, remember to skip the direct selection when the  user in China restarts, do not connect to WIFI or unplug the SIM card, because you will be called to log in to Google, if you do not link VPN, your router will stuck you on the Google login page. Then enter the mobile desktop environment, connect to WIFI or 4G, open the magisk app to update (note here, if you do not open the magisk update for the first time, it will cause the magisk  SafetyNet system security check can not pass) and then restart.

5.Open the magisk selection module, brush into my WIFI firmware package, now you can use the nethunter kernel perfectly.

```
The correct operation process: twrp>Download OOS>payload_dumper payload.bin>flash.sh or bat>adb sideload DJY XXX.zip>Reboot>Open magisk for the first time to connect to network to update for pass my SafetyNet Status Check>Reboot> Brush to my WIFI module > Start loading

```

6, For brush into kalifs-full.tar.xz Here I recommend three methods, the first and second are all use linux deploy to install, the third one is to use nethunter app to install. Official link https://build.nethunter.com/kalifs/kalifs-20190228/
The first
![pic](images/install1.JPG)
Second
![pic](images/install2.JPG)
Third
![pic](images/install3.jpg)

```
Note here that if you download arm64, amd64, i386 bit version of kalifs-full.tar.xz, you need to change the file name in the package to armhf. If you don't change it, nh terminal and nethunter will not be recognized and installed. The kernel has built-in busybox1.31, so there is no need to download the busybox installer.

```
# Update history

- [DJY0.1-DJY11] Fix many bugs, add HID attack support, add network card support, unlock mobile phone built-in AM/FM chip can receive AM/FM signal without using SDR, CP210x, FTDI, CH341 module. Unlock Bluetooth module support (Bluetooth attack), add the @simonpunk nethunter app usbarmy module, add and modify the @rithvikvibhu WIFI module for more support and fix support for the 9.0Pie system. Test system OP6T_O2_BETA_04

- [DJY11-DJY13] Fixed a lot of script errors, optimized kernel update, updated nethunter app, added kernel patch to permanently set selinux to permissive, updated WIFI firmware error script, updated busybox to 1.31, fixed the bug that busybox could not install 

- [DJY13-DJY15] Update nethunterapp, update nethunter-nh terminal, add update app into WIFI firmware package, delete WIFI firmware flash package extra code, add pn532 module, update kernel code compilation, repair HID attack occasionally can not be used .

(Because 15 or more have joined the osmcombb and openbts automatic environment scripts, they have violated the relevant China laws, so the kernel of 15+ or higher will not be announced)

- [DJY15-DJY17] Add Proxmark3 CDC driver, add osmcombb one-click environment configuration script, one-click brush script. Test system OP6T_O2_BETA_05

- [DJY17-DJY18] Add pppoe USB external driver to increase the function of sniffing router pppoe password, unlock the full function of mobile phone NFC, add amateur radio support, and optimize the kernel overall.

- [DJY18-DJY19] Add openbts+c118 one-click pseudo base station configuration script, join GSM Sniff WEB GUI interface ###Complete progress percent 70#####

# Kernel images and demo video for DJY11-13
HID Attack

![pic](images/HIDAattackSupport.jpg)

BluetoothattackSupport

![pic](images/BluetoothattackSupport.jpg)

C118+osmcombb

![pic](images/C118OSB.JPG)

mousejack

![pic](images/mousejackSupport.jpg)

HACKRF1

![pic](images/HACKRF1.jpg)

HACKRF2

![pic](images/HACKRF2.jpg)

RTL-SDR1

![pic](images/RTL-SDR1.jpg)

RTL-SDR2

![pic](images/RTL-SDR-KAL-900.jpg)

Wireless1

![pic](images/Wireless1.jpg)

Wireless2

![pic](images/Wireless2.jpg)

# DJY15+
C118+osmcomb  One-click configuration script

![pic](images/OSBGSMSniffSupport.png)

# DJY17-DJY19

Proxmark3 CDC driver support

![pic](images/Proxmark3CDCSupport.JPG)

# Related test video collection
- Bluetooth attack
http://www.bilibili.com/video/av45974214/

- C118--P1
https://www.bilibili.com/video/av45973153

- C118--P2
https://www.bilibili.com/video/av45973153/?p=2

- chameleon-Mini
http://www.bilibili.com/video/av45943906/

- PM3
https://www.bilibili.com/video/av45941948

- PPPOE sniff
https://www.bilibili.com/video/av45942786

- pn532
http://www.bilibili.com/video/av45945899/

- wifte and fluxion can not use fixed
https://www.bilibili.com/video/av45973380

- HID Aattack
https://www.bilibili.com/video/av43617250

- Wireless network card 722N
https://www.bilibili.com/video/av45943180

* Welcome to submit test screenshots and videos

# Common problems solution:
1、If the nethunter app and nh terminal use exceptions, please download OOS.

2、If the magisk SafetyNet status check does not work properly, please restore the boot image and rebrush the magisk https://github.com/topjohnwu/Magisk/releases

3、If you can't execute bootkali in the adb shell or Android shell, please rebrush the WIFI module.

4、if you use linux deploy installed kali, and can not start postgesql , please refer to the following code, mysql is the same.
``` 
nano /usr/sbin/update-rc.d
# Blacklist
# postgresql disabled (comment)

#Whitelist
postgresql enabled (add)
-----
than you need to grand permisson of postgresql
usermod -a -G aid_inet postgres 
service postgresql start
exit
bootkali
```
5、 If WIFITE and fluxion are not working properly, refer to https://www.bilibili.com/video/av45973380

6、If kalifs-full.tar.xz does not work properly with the new nethunter app, please refer to the temporary solution below. I will fix the Nethunter app later.

```
adb push kalifs-full.tar.xz /sdcard/ 
adb shell
su
mv /sdcard/kalifs-full.tar.xz /data/local/nhsystem/
cd /data/local/nhsystem/
xz -d kalifs-full.tar.xz
tar xvf kalifs-full.tar

```


# File md5 and hash

```
b4c66efc7fc076121997083a95bf8f96  com.google.zxing.client.android-4.7.7-107-1042.apk
411fb7a7439ef1db0be9f76bebb5c1d4  com.sonelli.juicessh_116_apps.evozi.com.apk
70c26e550fc6bc0c1d76098d9dce43e4  linuxdeploy-2.2.1-243.apk
201f288e4a3a27638828a367e106c720  marto.rtl_tcp_andro_20_apps.evozi.com.apk
9b7b226a66c71179d93e291695f17c00  nethunter-app-Pie.apk
686332a10c18d0e926ce7a6b338c3ef0  RFAnalyzer.apk
3eacb5ae172f968f04ecb7ca79bb388e  shadowsocksr-release.apk
5d2b490bc25056029d17ebd474da4587  Term-nh.apk
6bd10e7ec862203e7fa1d3282c0d278d  USBKeyboard.apk
9517c8f6df5d8569e8bea9c41d29adea  WiFi.apk

4305f92439c517ca102e7546c2932d4d0b587cef  com.google.zxing.client.android-4.7.7-107-1042.apk
5c388a3fdec49df7b19f8353270b41f4d2826225  com.sonelli.juicessh_116_apps.evozi.com.apk
ef26fd6ffda89525e3f591dcda1b613aa0dcf8a5  linuxdeploy-2.2.1-243.apk
205146887061c62e1a3fcfe60efb4665f153525d  marto.rtl_tcp_andro_20_apps.evozi.com.apk
8989b8d2adec9030edd772eb2cfc691fb14b8f6a  nethunter-app-Pie.apk
1d48c025e18eef1a9c69252bf2cfa3464f2d34bf  RFAnalyzer.apk
0092d68ce07135d587d1d041550a65807bc939ea  shadowsocksr-release.apk

8a4ae41b5ed727767cec9607e58e3ea53e9155af  Term-nh.apk
cba3e89c8a3b3a43572d58f737bba53d928d4913  USBKeyboard.apk
2847a4acf3f6022f98e95d630c10c5bbf05bf136  WiFi.apk


a13cfb2dd89f8c4c34c7f74ba0032bb4  Wireless_Firmware_for_Nethunter-v4.0


93abfd9bec69180ff5a08e85f4488075ffd40d86  Wireless_Firmware_for_Nethunter-v4.0

79a75c5452327d151765bb698dc0e210  DJY Nethunter KernelV15.zip


5130697b30db4ec8e6a2c1f456aa80e0729d8988  DJY Nethunter KernelV15.zip



cdf3700352b8b08e99d34bda0dcf6271  busybox8£¨1.31£©


9ce94e14952a6ecf444f67636e81b281cca5daf2  busybox8£¨1.31£©

e09ea86bcb0eb8f30bc4bcc5703b2928  flash.bat
e09ea86bcb0eb8f30bc4bcc5703b2928  flash.sh
c1f55f501b5c628199ca3c0b200bd8d7  Payload_Dumber_x64 -win.zip
94ee67ddc8ae426beb3a6f8a8e361191  payload_dumper-linux.zip

9d315088a79a36ac08e29140bed21d1293205da1  flash.bat
9d315088a79a36ac08e29140bed21d1293205da1  flash.sh
542bd47de3e49848b7ba6ae4e07c7d07f45a40e7  Payload_Dumber_x64 -win.zip
7c97f484ce3c2b9174d107572f0e420b566643dc  payload_dumper-linux.zip


```
- If you find out that MD5 and Hash are compared not correct, pay attention to whether someone has modified and implanted a virus.


# Relate coed and moudle list:

Thanks to @simonpunk for thrr support of HID patching. Related build code links used:

https://github.com/simonpunk/nethunter-app

https://github.com/pelya/android-keyboard-gadget

Thanks to @HolyAngle for the excellent kernel project

https://gitlab.com/HolyAngel/op6

Thanks to @rithvikvibhu for the Magisk WIFI module

# Contact information
Kali linux QQ chat number: 712420808 (Welcome everyone join and communite to us)

Telegram group:https://t.me/nethunter666
If you want to reprint please note the source.Thank you. ^ _ ^
                  











