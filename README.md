#### Nvidia Graphics Driver Installation Documentation on Manjaro

`sudo pacman -S yay`

`yay -Syu`

`yay -S base-devel`

Check kernel version: `uname -a`

If kernel version does not match with Nvidia drivers, downgrade to LTS kernel from Manjaro Settings Manager: `Linux54` / `Linux 5.4.67-1`

Update grub settings to select kernel version on boot:
   - `sudo vim /etc/default/grub`
   - `GRUB_TIMEOUT_STYLE=menu`
   - `sudo update-grub`

Install appropriate Nvidia driver: `yay -S linux54-nvidia-440x`

Steam needs 32-bit support. Install with `yay -S lib32-nvidia-utils`

Instal Optimus Manager: `yay -S optimus-manager optimus-manager-qt`

Automatically start on boot: `sudo systemctl enable optimus-manager`

Restart

Open Optimus Manager and apply the following settings:
- General -> Launch at startup
- Optimus -> Starttup mode: Nvidia

Open NVIDIA X Server Settings and apply the following settings:
- OpenGL Settings -> Image Settings: High Performance
- PowerMizer -> Preferred Mode: Prefer Maximum Performance

Set CPU on Performance Mode:  `sudo echo performance | tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor`

Reboot




