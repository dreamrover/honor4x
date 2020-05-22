## honor4x
华为荣耀畅玩4x全网通手机（Che1-CL20）解锁、升级、刷入twrp及LineageOS 

此款手机是首款支持4G全网通的经典千元机，搭载的CPU是高通骁龙410，虽然支持64位，但64位模式并未开启，所以系统和应用只能安装32位的。

手机原装系统是EMUI 3.0 (Android 4.4) V100R001CHNC00B288，如果系统不经升级直接刷入LineageOS 15.1 (Android 8.1)，会出现无法挂断电话的问题；

所以需要升级到官方的EMUI 4.0.1 (Android 6.0) C00B440，但是由于存储分区差别很大（如EMUI3.0没有erecovery等），不能直接从EMUI3.0升级至4.0.1，需先升级到EMUI 3.1 (Android 5.1) C00B316，再升级至EMUI4.0.1；升级方法见Che1-CL20C00B316 版本升级指导书.pdf（指导书中没说B288可以升级至B316，但实测可以）。

EMUI3.1下载地址（貌似失效了）：https://club.huawei.com/thread-6617843-1-1.html

http://download-c.huawei.com/download/downloadCenter?downloadId=59705&version=194189&siteCode=

EMUI4.0.1下载地址：https://club.huawei.com/thread-11625493-1-1.html

http://update.hicloud.com:8180/TDS/data/files/p3/s15/G1050/g223/v78343/f1/full/update.zip

## 解锁
* adb reboot bootloader
* fastboot oem unlock 0483614783261389（替换成当前手机的解锁码）
* fastboot oem get-bootinfo

## 刷入TWRP
* adb reboot bootloader
* fastboot flash recovery twrp_3.2.3-0_O_cherry.img /
* fastboot reboot
* adb reboot recovery

也可以不刷入flash，直接启动至TWRP：
* fastboot boot twrp_3.2.3-0_O_cherry.img

## 刷入第三方ROM、GAPPS、Root及Xposed
在TWRP中，进入advance->sideload：
* adb sideload lineage-15.1-20200225-nightly-cherry-signed.zip
* adb sideload open_gapps-arm-8.1-pico-20200325.zip
* adb sideload addonsu-15.1-arm-signed.zip
* adb sideload xposed-v90-sdk27-arm-beta3.zip
* adb reboot

也可以在TWRP中点击Install，从SD卡中安装上述zip包

## 安装必要APP
安装Xposed APP，需授予root权限：
* adb install XposedInstaller_3.1.5.apk

若距离传感器失灵导致接打电话黑屏，需安装SensorDisabler，在Xposed中启用此模块，然后在模块中将Proximity设置为固定值：
* adb install SensorDisabler.apk

墙内用户重置此URL以免Wifi显示链接失败：
* adb shell "settings put global captive_portal_https_url https://captive.lineageos.org.cn/generate_204";

安装RootExplorer（CX文件管理器和FV文件管理器也值得推荐）：
* adb install RootExplorer_v4.2.4.apk
* adb reboot

（de.robv.android.xposed.installer_v33_36570c.apk是用于Android 4.4的，已升级或刷入其他系统不要安装此apk；recovery.img是EMUI3.0的原厂recovery。）
