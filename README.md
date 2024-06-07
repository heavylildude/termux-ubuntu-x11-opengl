Disable Phantom Process Killer Android ::

https://maheshtechnicals.com/fix-termux-error-process-completed-signal-9-disable-phantom-process-killer-in-android-12-13/



Termux setup ::
```
pkg update
pkg upgrade
pkg install x11-repo
pkg install termux-x11-nightly
pkg install tur-repo
pkg install pulseaudio
pkg install proot-distro
pkg install wget
pkg install git
```

Termux X11 ::

https://github.com/termux/termux-x11


Recommended Ubuntu Automated Script ::

https://github.com/modded-ubuntu/modded-ubuntu


Hardware Acceleration Termux ::

## 1. Install packages in Termux
```
pkg install mesa-zink virglrenderer-mesa-zink vulkan-loader-android virglrenderer-android
```

## 2. Initialize graphical server in Termux: 

* Vulkan (ZINK):
```
MESA_NO_ERROR=1 MESA_GL_VERSION_OVERRIDE=4.3COMPAT MESA_GLES_VERSION_OVERRIDE=3.2 GALLIUM_DRIVER=zink ZINK_DESCRIPTORS=lazy virgl_test_server --use-egl-surfaceless --use-gles &
```
* OpenGL (VIRGL):
```
virgl_test_server_android &
```
* [Turnip (Adreno GPU 6XX/7XX compatible only)](https://www.reddit.com/r/termux/comments/19dpqas/proot_linux_only_dri3_patch_mesa_turnip_driver/)
It is not needed to initialize any graphical server. Follow the steps described in the reddit post. As as summary:

  1. Download Turnip Driver: [mesa-vulkan-kgsl_23.3.0-devel-20230905_arm64.deb](https://drive.google.com/file/d/1f4pLvjDFcBPhViXGIFoRE3Xc8HWoiqG-/view?usp=drive_link)
  2. Install it in proot-distro (for example in Debian the command is as follows)
```
sudo dpkg -i mesa-vulkan-kgsl_23.3.0-devel-20230905_arm64.deb
```
  In case you want to remove the driver: 
```
sudo dpkg -r mesa-vulkan-drivers:arm64
```

* For VIRGL and ZINK: 
```
GALLIUM_DRIVER=virpipe MESA_GL_VERSION_OVERRIDE=4.0 program
```
* For TURNIP: 
```
MESA_LOADER_DRIVER_OVERRIDE=zink TU_DEBUG=noconform program
```


Gstreamer ::

https://gstreamer.freedesktop.org/documentation/installing/on-linux.html?gi-language=c


Gstreamer Debian Ubuntu ::
```
apt-get install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-bad1.0-dev gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-tools gstreamer1.0-x gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-gtk3 gstreamer1.0-qt5 gstreamer1.0-pulseaudio
```

>> after all installation use "bash startme.sh" from termux and "bash startx11.sh" from ubuntu


Cool VL Viewer Arm64 ::

https://sldev.free.fr/index.php?page=download
