
# 蓝牙 打印机
```
# 安装 
sudo pacman -S bluez bluez-utils cups cups-pdf system-config-printer

# kde printer
print-manager

# 开机启动
sudo systemctl enable bluetooth.service

sudo systemctl enable avahi-daemon.service
# 立即开启

sudo systemctl start bluetooth.service

sudo systemctl enable cups.service
sudo systemctl start cups.service

vim /etc/cups/cups-pdf.conf
sudo sed -i '$a\Out /home/${USER}/PDF' /etc/cups/cups-pdf.conf

wqy-zenhei wqy-microhei wqy-microhei-lite noto-fonts noto-fonts-cjk noto-fonts-emoji 
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

pamac-nosnap
pamac-all

```
## Arch Amd

mesa xf86-video-amdgpu xf86-video-ati libva-mesa-driver vulkan-radeon 
mesa-vdpau

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
# 缩略图
```
sudo pacman -S tumbler webp-pixbuf-loader poppler-glib ffmpegthumbnailer freetype2 libgsf gnome-epub-thumbnailer f3d

tumbler：图像文件。在某些情况下，还必须安装此软件才能将缩略图功能扩展到其他文件类型。
webp-pixbuf-loader：.webp图像
poppler-glib：Adobe.pdf文件
ffmpegthumbnailer：视频文件
freetype2：字体文件
libgsf：.odf文件

totem：视频文件和标记的音频文件（仅限GNOME 文件和 Caja）
evince或atril：.pdf文件
gnome-epub-thumbnailer：.epub和.mobi电子书文件
mcomix AUR：.cbr漫画档案
folderpreview AUR：文件夹缩略图
f3d：3D 文件，包括 glTF、stl、step、ply、obj、fbx。
```

有时不显示视频缩略图。要解决这个问题（如nautilus 上没有视频缩略图中所述，您必须安装ffmpegthumbnailer、gst-libav、gst-plugins-ugly，并删除~/.cache/thumbnailsfails/gnome-thumbnail-factory/.

ffmpegthumbnailer gst-libav gst-plugins-ugly

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