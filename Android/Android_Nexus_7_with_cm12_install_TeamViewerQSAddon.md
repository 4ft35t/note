# Android Nexus 7 with cm12 install TeamViewerQSAddon

启动 TeamViewer Host/TeamView QuickSupport 会提示安装远程控制插件，确认会自动下载。
## 正常安装
只显示应用未安装
## adb/pm
```bash
adb install TeamViewerQSAddon.apk
```
或

```bash
pm install /sdcard/Download/TeamViewerQSAddon.apk
```
会报同一个错误
`INSTALL_FAILED_INVALID_INSTALL_LOCATION`

同时 logcat 输目录
`/data/data/com.teamviewer.quicksupport.addon.aosp/`不存在错误。

中间尝试过手工创建目录，并复制 apk 文件到

`/data/apk/com.teamviewer.quicksupport.addon.aosp-1`
并不生效。

## 解决方案
把 apk 安装成系统应用

1. adb shell
2. su
3. mount -o rw,remount /system
4. cp /sdcard/Donwload/TeamViewerQSAddon.apk /system/app/
5. chmod +r /system/app/TeamViewerQSAddon.apk
6. mount -o ro,remount /system
7. reboot to recovery and wipe cache and Dalvik cache and reboot

