## honor4x
��Ϊ��ҫ����4xȫ��ͨ�ֻ���Che1-CL20��������������ˢ��twrp��LineageOS 

�˿��ֻ����׿�֧��4Gȫ��ͨ�ľ���ǧԪ�������ص�CPU�Ǹ�ͨ����410����Ȼ֧��64λ����64λģʽ��δ����������ϵͳ��Ӧ��ֻ�ܰ�װ32λ�ġ�

�ֻ�ԭװϵͳ��EMUI 3.0 (Android 4.4) V100R001CHNC00B288�����ϵͳ��������ֱ��ˢ��LineageOS 15.1 (Android 8.1)��������޷��Ҷϵ绰�����⣻

������Ҫ�������ٷ���EMUI 4.0.1 (Android 6.0) C00B440���������ڴ洢�������ܴ���EMUI3.0û��erecovery�ȣ�������ֱ�Ӵ�EMUI3.0������4.0.1������������EMUI 3.1 (Android 5.1) C00B316����������EMUI4.0.1������������Che1-CL20C00B316 �汾����ָ����.pdf��ָ������û˵B288����������B316����ʵ����ԣ���

EMUI3.1���ص�ַ��ò��ʧЧ�ˣ���https://club.huawei.com/thread-6617843-1-1.html

http://download-c.huawei.com/download/downloadCenter?downloadId=59705&version=194189&siteCode=

EMUI4.0.1���ص�ַ��https://club.huawei.com/thread-11625493-1-1.html

http://update.hicloud.com:8180/TDS/data/files/p3/s15/G1050/g223/v78343/f1/full/update.zip

## ����
* adb reboot bootloader
* fastboot oem unlock 0483614783261389���滻�ɵ�ǰ�ֻ��Ľ����룩
* fastboot oem get-bootinfo

## ˢ��TWRP
* adb reboot bootloader
* fastboot flash recovery twrp_3.2.3-0_O_cherry.img /
* fastboot reboot
* adb reboot recovery
Ҳ���Բ�ˢ��flash��ֱ��������TWRP��
* fastboot boot twrp_3.2.3-0_O_cherry.img

## ˢ�������ROM��GAPPS��Root��Xposed
��TWRP�У�����advance->sideload��
* adb sideload lineage-15.1-20200225-nightly-cherry-signed.zip
* adb sideload open_gapps-arm-8.1-pico-20200325.zip
* adb sideload addonsu-15.1-arm-signed.zip
* adb sideload xposed-v90-sdk27-arm-beta3.zip
* adb reboot
Ҳ������TWRP�е��Install����SD���а�װ����zip��

## ��װ��ҪAPP
��װXposed APP��������rootȨ�ޣ�
* adb install XposedInstaller_3.1.5.apk
�����봫����ʧ�鵼�½Ӵ�绰�������谲װSensorDisabler����Xposed�����ô�ģ�飬Ȼ����ģ���н�Proximity����Ϊ�̶�ֵ��
* adb install SensorDisabler.apk
ǽ���û����ô�URL����Wifi��ʾ����ʧ�ܣ�
* adb shell "settings put global captive_portal_https_url https://captive.lineageos.org.cn/generate_204";
��װRootExplorer��CX�ļ���������FV�ļ�������Ҳֵ���Ƽ�����
* adb install RootExplorer_v4.2.4.apk
* adb reboot

��de.robv.android.xposed.installer_v33_36570c.apk������Android 4.4�ģ���������ˢ������ϵͳ��Ҫ��װ��apk��recovery.img��EMUI3.0��ԭ��recovery����