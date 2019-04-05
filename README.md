<div align=center><img src=images/LOGO.png width=100% ></div>


# 前言

大家好我是来自中国的业余菜鸟极客打酱油。DJY Nethunter Kernel 是一个一加6和6T全功能的修补内核，支持hackrf，RTL-SDR，mousejack，osmcombb+C118+openbts，蓝牙攻击，外接红外模块，外接OTG网线进行pppoe路由器密码嗅探，OTG外接多种无线网卡RTX系列，MT7601系列，ahk9系列，htc系列。Proxmark3 CDC HID 驱动支持，chameleon-Mini驱动支持。这个项目是免费分享的，并不需要付费，谨防某些骗子团伙（某眼团队）拿来出售，请注意效验MD5值和hash值。为了编译这个内核我重复刷机上百次，解决刷入内核无法打开WIFI，无法使用adb shell，无法外接USB设备，黑屏，卡在第一屏等等错误....进行长时间的测试，如果有bug问题欢迎反馈。如果你觉得好用请给我一个**star** 你的支持是我最好的动力。

在这里我还要说一点，对于一些loser 傻逼，我想说我不欠你，你可以使用它，或者你可以选择不用，但不要像疯狗一样咬我。我免费分享给某些人用，你不但连句谢谢感激之类的话都没有（挡住某些人赚钱），你还要倒打一耙来骂我，贬低我，甚至还有些傻逼举报了我两个千人群聊，害我被封有意义吗？我在这里祝举报我的人生儿子没屁眼，喝水塞牙，每天都倒霉，还不起支付宝花呗，借呗，京东微贷，天天来大姨妈等等一系列倒霉事情。吃屎啦你！！！！！！

****
其他语言(翻译来自@Noob-DaoXin 道心): [English](README_EN.md)

# 目录
* [Install](#Install)
* [更新历史](#更新历史)
* [内核图片和视频演示DJY11-13](#内核图片和视频演示DJY11-13)
* [DJY15](#DJY15)
* [DJY17-DJY19](#DJY17-DJY19)
* [相关测试视频集合](#相关测试视频集合)
* [常见问题解决](#常见问题解决)
* [文件md5sum](#文件md5sum)
* [相关代码和模块感谢列表](#相关代码和模块感谢列表)
* [联系方式](#联系方式)
# Install

1、到 https://twrp.me/ 下载与你设备相关的twrp，然后到 https://www.oneplus.com/support/softwareupgrade/ 选择你的设备下载系统（这里需要注意的是，国内用户需要**翻墙**才能下载OOS，为什么这里不推荐使用一加的HOS系统呢？因为HOS国内系统在某些权限功能上面做了一些限制，所以会出现某些命令和终端不能正常使用的现象，但是也是可以用的，就是不够完美，这里推荐使用OOS）

2、使用我上传的payload_dumper win or linux 解压压缩包里面的payload.bin固件，然后刷入twrp，挂载所有分区，清理userdate分区，然后在选择清理所有分区，再使用我上传flash.sh or bat 刷入所有的镜像。这样就是全新的OOS了。

3、刷完之后，在刷入twrp，然后选择adb sideload 推送我的DJY Nethunter Kernel。
```
adb sideload DJY XXX.ZIP
```
4、然后重启到系统，国内用户重启的时候记得直接选择跳过，不要连WIFI或者拔掉SIM卡，因为你连了网他就会叫你登录谷歌，如果你路由器没有链接VPN的话会导致你卡死在谷歌登录页面。然后进入到了手机桌面环境，连接WIFI或4G，打开magisk app 进行更新（这里需要注意的是，如果你在第一次不打开magisk更新的话，会导致magisk SafetyNet 系统安全检查无法通过）然后重启。

5、打开magisk 选择模块，刷入我的WIFI固件包，现在你就可以完美使用nethunter的内核了。
```
正确操作流程：twrp>下载OOS>payload_dumper payload.bin>flash.sh or bat>adb sideload DJY XXX.zip>重启>第一次打开magisk进行联网更新来通过SafetyNet 状态检查>重启>刷入我的WIFI模块>开始装逼使用
```
6、关于刷入kalifs-full.tar.xz这里我推荐三种方法，第一第二种都是使用linux deploy来安装，第三种使用nethunter app安装。官方链接 https://build.nethunter.com/kalifs/kalifs-20190228/ 
第一种
![pic](images/install1.JPG)
第二种
![pic](images/install2.JPG)
第三种
![pic](images/install3.jpg)

```
这里需要注意的是如果你下载arm64，amd64，i386位版本的kalifs-full.tar.xz，你需要将包内文件名更改为armhf，如果不更改，那么nh终端和nethunter将无法识别和安装。内核已经内置了busybox1.31，所以不需要下载busybox安装器

```

# 更新历史

- [DJY0.1-DJY11] 修复众多BUG，添加HID attack支持，添加网卡支持，解锁手机内置AM/FM芯片不使用SDR即可接收AM/FM信号，CP210x，FTDI，CH341 模块.解锁蓝牙模块支持（蓝牙攻击），添加@simonpunk nethunter app usbarmy模块，添加修改@rithvikvibhu WIFI模块以便增加更多的支持并修复对9.0Pie系统的支持。测试系统OP6T_O2_BETA_04

- [DJY11-DJY13] 修复大量错误脚本错误，优化更新内核，更新nethunter app，添加内核补丁将selinux 永久设置为 permissive，更新WIFI固件错误脚本，更新busybox为1.31，修复busybox无法安装bug

- [DJY13-DJY15] 更新nethunterapp，更新nethunter-nh终端，添加更新app进WIFI固件包，删错WIFI固件刷机包多余代码，添加pn532模块，整体更新内核代码编译，修复HID攻击偶尔不能使用的情况。

（由于15以上加入了osmcombb和openbts自动环境脚本，已经触犯了国内相关法律，所以15以上版本内核不会公布）

- [DJY15-DJY17] 添加Proxmark3 CDC驱动，添加osmcombb一键环境配置脚本，一键刷机脚本。测试系统OP6T_O2_BETA_05

- [DJY17-DJY18] 添加pppoe USB外接驱动以增加嗅探路由器pppoe密码的功能，解锁手机NFC全功能，添加业余无线电台支持，整体优化更新内核。

- [DJY18-DJY19] 添加openbts+c118 一键伪基站配置脚本，加入GSM Sniff WEB GUI界面 ###完成进度百分之100#####

- [DJY15-3] 修复nethunter app删除kali.tar.xz错误并加入对 i386 amd64 arm64动chroot的支持。添加大量固件，将WIFI固件从2008更新到2019，内核代码整体更新编译，加入一些常用的apk，更新终端app,更新app工具链，修复更新busybox没正常安装问题，添加开机动画（如果有需要更改的可以解压WIFI压缩包替换system/media/bootanimation.zip 文件)。以上代码全是最新代码编译使用gcc 8.2.1 studio 3.5 canary7 测试系统：官方OOS稳定版和OOS beta 5-7。新增编译的最新HID攻击app，这个app可以不在chroot 安装kali的下使用HID攻击，但是需要内核支持。（现在已经完美支持 limeSDR HACKRF USRP UHD驱动检测）

- [DJY23] openbts5.0 已经编译成功，现在可以使用1+6和1+6T 搭建小型GSM基站测试网络，支持hackrf C118 RTL-SDR 发射和接收内容 ~~（在信号范围内可以打电话发短信，理论上来讲还支持USRP和limeSDR，但是没设备无法测试）~~ (hackrf limeSDR USRP UHD 已经通过测试)

# 内核图片和视频演示DJY11-13
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

HACKRF-UHD

![pic](images/hackrf-UHD.JPG)

LimeSDR-UHD

![pic](images/limesdr-UHD.jpg)

USRP-UHD

![pic](images/USRP-UHD.jpg)

USRP1-UHD

![pic](images/USRP1-UHD.jpg)


# DJY15
C118+osmcombb 一键配置脚本

![pic](images/OSBGSMSniffSupport.png)

# DJY17-DJY19

Proxmark3 CDC驱动支持

![pic](images/Proxmark3CDCSupport.JPG)


# 相关测试视频集合
- 蓝牙攻击
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

- wifte和fluxion不能使用修复
https://www.bilibili.com/video/av45973380

- HID Aattack
https://www.bilibili.com/video/av43617250

- 无线网卡722N
https://www.bilibili.com/video/av45943180

- 开机动画
https://t.me/nethunter666/2688


* 欢迎提交各类测试截图和视频

# 常见问题解决
1、如果nethunter app 和 nh 终端使用异常请下载OOS。

2、如果magisk SafetyNet 状态检查不能正常执行请还原boot镜像在从新刷入magisk https://github.com/topjohnwu/Magisk/releases

3、如果无法在adb shell 或者安卓shell里面不能正常执行 bootkali 请重新刷入WIFI模块。

4、如果使用linux deploy 安装的 kali，如果无法启动postgesql请参考以下代码，mysql同理。

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
5、如果WIFITE和fluxion不能正常使用参考 https://www.bilibili.com/video/av45973380

~~6、如果新版nethunter app 无法安装正常安装 kalifs-full.tar.xz 请参考以下代码，我会在有空的时候修复nethunter app(已经修复)~~


~~adb push kalifs-full.tar.xz /sdcard/ 
adb shell
su
mv /sdcard/kalifs-full.tar.xz /data/local/nhsystem/
cd /data/local/nhsystem/
xz -d kalifs-full.tar.xz
tar xvf kalifs-full.tar~~

7、如果无法使用新的HID攻击app。请在安卓shell （root权限下面）执行以下任意命令：

```
setprop sys.usb.config reset
setprop sys.usb.config win,hid
setprop sys.usb.config win,mass_storage
setprop sys.usb.config win,rndis
setprop sys.usb.config win,hid,mass_storage
setprop sys.usb.config win,rndis,hid
setprop sys.usb.config win,rndis,mass_storage
setprop sys.usb.config win,rndis,hid,mass_storage
setprop sys.usb.config mac,hid
setprop sys.usb.config mac,mass_storage
setprop sys.usb.config mac,ecm
setprop sys.usb.config mac,hid,mass_storage
setprop sys.usb.config mac,ecm,hid
setprop sys.usb.config mac,ecm,mass_storage
setprop sys.usb.config mac,ecm,hid,mass_storage

```



# 文件md5sum

```
abcca492a40a7a8559b28056c3cf348f  DJY15-3.zip
327cc32315a3e059924a01298f662c0c  DJY-WIFI-firmware-APP-7.0-beta.zip
ee63074fae0db4136c50b15a0d85a2ca  flash.bat
e09ea86bcb0eb8f30bc4bcc5703b2928  flash.sh
c1f55f501b5c628199ca3c0b200bd8d7  Payload_Dumber_x64 -win.zip
94ee67ddc8ae426beb3a6f8a8e361191  payload_dumper-linux.zip

5deaffc43baa6c62c92719d0342cfd45  andprox-2.0.4.apk
a9e233213fabc47e60c982ce20215e4f  bs.Avare.ADSB_80_apps.evozi.com.apk
106ccb9b94016d55bc9f648047a84dc6  com.comthings.pandwarf_10239_apps.evozi.com.apk
3e3b7c5380a2650ebbbe9765d0ec2827  com.google.zxing.client.android-4.7.7-107-1042.apk
4d3e96fb430f5b6b3ff7783ca112f404  com.sdr_labs.sdroid_1307_apps.evozi.com.apk
806e607a7e8b798ca8a659d02e625610  com.softwarebakery.drivedroid_105000_apps.evozi.com.apk
411fb7a7439ef1db0be9f76bebb5c1d4  com.sonelli.juicessh_116_apps.evozi.com.apk
6d9913ad3fb1d7442ed6c55809f2a501  cSploit-nightly.apk
40ba3df5392e191038ae64d393ffdd13  linuxdeploy-2.2.1-243.apk
015ce640b07bec8a81e0daca25f88cc7  LuckyPatchers.com_Official_V8.2.3.apk
f6fd10fe6fd6aaec5361ba57e61e66dc  marto.androsdr2_39_apps.evozi.com.apk
201f288e4a3a27638828a367e106c720  marto.rtl_tcp_andro_20_apps.evozi.com.apk
c0f9a8a5861aadd4a325ab9374568f12  nethunter-app-Pie.apk
0582c876a40cde26525dd3bc02694da8  org.hak5.pineappleconnector_2_apps.evozi.com.apk
686332a10c18d0e926ce7a6b338c3ef0  RFAnalyzer.apk
3eacb5ae172f968f04ecb7ca79bb388e  shadowsocksr-release.apk
5e1c03901f7f04bc1c9f458b721b8760  Term-nh.apk
6bd10e7ec862203e7fa1d3282c0d278d  USBKeyboard.apk
9517c8f6df5d8569e8bea9c41d29adea  WiFi.apk
5292442051bf19b2c0f67fcdbfd9f9e8  zAnti3.18.apk

c8295ecd5932cad08c3dfbb9bfce6394  bootanimation.zip(开机动画，有需要更改的可以自己替换)

d504130c72d92213e8f464511a47abe9  busybox8（1.32）





```
- 如果你发现MD5对比不对，注意是否有人修改了并且植入了病毒



# 相关代码和模块感谢列表

感谢@simonpunk 对HID修补的大力支持。用到的相关构建代码链接：

https://github.com/simonpunk/nethunter-app

https://github.com/pelya/android-keyboard-gadget

感谢@HolyAngel 的优秀内核项目

https://gitlab.com/HolyAngel/op6

感谢@rithvikvibhu 感谢对Magisk WIFI模块做出的贡献

@draguve

https://github.com/draguve/droidducky-app

这是我已经修复的内核源码，已修复HID和WIFI

https://github.com/johanlike/-DJY-nethunter-kernel-source


# 联系方式
kali linux QQ交流群：712420808 （欢迎各种大佬萌新进群吹水）

电报群组：https://t.me/nethunter666
如果你需要转载请注明出处谢谢.
