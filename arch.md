
# 蓝牙 打印机
```
# 安装 
sudo pacman -S bluez bluez-utils cups cups-pdf fuse2 git flatpak print-manager system-config-printer
firefox-i18n-zh-cn
fuse2 
fuse3
exfat-utils dosfstools #查一下安装系统
exfatprogs #查一下安装系统
plasma-firewall firewalld

```
## flatpak
```
sudo flatpak remote-modify flathub --url=https://mirror.sjtu.edu.cn/flathub
```
# 使用bios时间,同步Windows
```
timedatectl set-local-rtc 1
```

# 开机启动
```
sudo systemctl enable firewalld.service
sudo systemctl enable bluetooth.service
sudo systemctl enable avahi-daemon.service
sudo systemctl enable cups.service
```
# 立即开启
```
sudo systemctl start bluetooth.service

sudo systemctl start cups.service

vim /etc/cups/cups-pdf.conf
sudo sed -i '$a\Out /home/${USER}/PDF' /etc/cups/cups-pdf.conf
```
# Fonts
```
wqy-zenhei wqy-microhei wqy-microhei-lite wqy-bitmapfont 
noto-fonts noto-fonts-cjk noto-fonts-emoji 
adobe-source-han-sans-cn-fonts adobe-source-han-serif-cn-fonts 
```
# fcitx5
```
fcitx5-im fcitx5-chinese-addons

sudo vim /etc/environment

GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
SDL_IM_MODULE=fcitx
INPUT_METHOD=fcitx
GLFW_IM_MODULE=ibus


sudo sed -i '$a\GTK_IM_MODULE=fcitx\nQT_IM_MODULE=fcitx\nXMODIFIERS=@im=fcitx\nSDL_IM_MODULE=fcitx\nINPUT_METHOD=fcitx\nGLFW_IM_MODULE=ibus' /etc/environment


/home/${USER}/t.txt
```
# ibus
```
sudo pacman -S ibus ibus-libpinyin

/etc/environment

GTK_IM_MODULE=ibus
QT_IM_MODULE=ibus
XMODIFIERS=@im=ibus

sudo sed -i '$a\GTK_IM_MODULE=ibus\nQT_IM_MODULE=ibus\nXMODIFIERS=@im=ibus' /etc/environment

```
# 个人目录
```
export LANG=en_US
xdg-user-dirs-gtk-update
export LANG=zh_CN.UTF-8
```

# yay
```
sudo pacman -S --needed base-devel git

git clone https://aur.archlinux.org/yay.git

makepkg -si

pamac-aur
google-chrome

```
## Arch Amd
```
mesa xf86-video-amdgpu lib32-mesa vulkan-radeon lib32-vulkan-radeon
libva-mesa-driver lib32-libva-mesa-driver mesa-vdpau lib32-mesa-vdpau
```


# Gnome扩展
```
sudo pacman -S gpaste gnome-shell-extension-appindicator

```
# 交换文件
```
swapFile(){
    #创建一个 32 GiB 的交换文件:
    echo "创建32G交换文件"
    sudo dd if=/dev/zero of=/swapfile bs=1M count=32k status=progress && sudo chmod 0600 /swapfile
    
    sudo mkswap -U clear /swapfile
    sudo swapon /swapfile && sudo sed -i '$a\/swapfile none swap defaults 0 0' /etc/fstab
    
    # sleep 5
    # sudo reboot
    RReboot

}
```

----------------------------
# kde-applications
```
gwenview spectacle dragon partitionmanager
arianna colord-kde kamera kcolorchooser koko kolourpaint kruler okular skanlite
```

# 缩略图
## Dolphin File previews
```
kdegraphics-thumbnailers: Image files, PDFs and Blender application files.
kimageformats5: Gimp .xcf files
libheif: HEIF files
qt5-imageformats : .webp, .tiff, .tga, .jp2 files
resvgAUR: Fast and accurate SVG image thumbnails
kdesdk-thumbnailers: Plugins for the thumbnailing system
ffmpegthumbs: Video files (based on ffmpeg)
raw-thumbnailerAUR: .raw files
taglib : Audio files
kde-thumbnailer-apkAUR: Android package files
```
在“设置”>“配置 Dolphin...”>“常规”>“预览”中启用所需文件类型的预览显示。
```
sudo pacman -S kdegraphics-thumbnailers kimageformats5 libheif kdesdk-thumbnailers ffmpegthumbs taglib 
```


# WPS
```
sudo mkdir /usr/share/fonts/wps-fonts
sudo mv ttf-wps-fonts/* /usr/share/fonts/wps-fonts
sudo chmod 644 /usr/share/fonts/wps-fonts/*
sudo fc-cache -vfs


sudo cp -v /usr/lib/libtiff.so.6.0.2 /usr/lib/libtiff.so.5
```

# mutil
```
/etc/pacman.conf
```
# NVIDIA
## 1安装驱动
```
nvidia  (for use with the linux kernel) 
nvidia-lts (for use with the linux-lts kernel)
nvidia-dkms (for all other kernels)

lib32-nvidia-utils


```
## 5
kms从HOOKS数组中删除/etc/mkinitcpio.conf并重新生成 initramfs。这将阻止 initramfs 包含该nouveau模块，确保内核在早期启动期间无法加载该模块。

