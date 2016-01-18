# 带 PIE 选项编译 Android netcat 

```sh 
git clone https://github.com/CyanogenMod/android_external_netcat

cd android_external_netcat
mkdir jni

cat>jni/Application.mk<<EOF
APP_ABI := armeabi-v7a
APP_STL := stlport_static
APP_PLATFORM := android-21
EOF

echo "LOCAL_CFLAGS += -pie -fPIE" >> Android.mk
echo "LOCAL_LDFLAGS += -pie -fPIE" >> Android.mk

/path/to/ndk/ndk-build APP_BUILD_SCRIPT=Android.mk
```

