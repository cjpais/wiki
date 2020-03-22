---
description: Some notes on install. Needs to be cleaned up
---

# Arch Linux



* Ok burn iso to flash drive. No problem. dd works great and /dev/**w**disk2 is lit
* She boots!
* Ok time to do wireless…
  * Basically need to connect to my wifi. I’ve only got 1 wifi card. `ip link set wlan0 up`
    * After install this became wlp5s0
  * Check it can scan `iwlist wlan0 scan`
  * Connect to my wifi `wpa_supplicant -B -i wlan0 -c <(wpa_passphrase cjwifi thisismypassword)`
    * basically wpa\_supplicant will help connect to wifi with wpa2 passphrase which is probably most routers default. I just played around until it worked. Yay technology!
    * wpa\_passphrase generates text that you are gonna shove into wpa\_supplicant to connect to your wifi
  * -B - Fork into background.
  * -c filename - Path to configuration file.
  * -i interface - Interface to listen on.
  * needed to run `dhcpcd wlan0` to get DHCP on the wlan interface
  * ping worked!
  * Well I need wifi at boot. Sym link `ln -s /usr/share/dhcpcd/hooks/10-wpa_supplicant /usr/lib/dhcpcd/dhcpcd-hooks/`
  * Create config for wpa\_supplicant to read on boot `wpa_passphrase cjwifi thisismypassword > /etc/wpa_supplicant/wpa_supplicant.conf`
* Create partitions. The wiki is confusing but ok. Took too long Want it to look like /dev/sda1 260M EFI System \(1\) /dev/sda2 32G Linux filesystem \(default\) /dev/sda3 4G Linux swap \(19\) /dev/sda4 430G Linux filesystem \(default\) basically: fdisk g - create for gpt n - new partition - paritition 1 - default start sector +260M - 260MB in size t - change partition type 1 - EFI n +32G n +4G n t 1 1 t 3 19
  * Now format those motherfuckers! mkfs.fat -F32 /dev/sda1 mkfs.ext4 /dev/sda2 mkfs.ext4 /dev/sda4
  * Swap mkswap /dev/sda3 swapon /dev/sda3
  * Mount them respectively mount /dev/sda2 /mnt mkdir /mnt/efi
  * get off the usb bro cmon `arch-chroot /mnt`
  * pacstrap me bro `pacstrap /mnt base linux linux-firmware vim openssh dhcpcd wpa_supplicant`
  * install grub
* hostname
* timezone….
* Booted: TIPS for services!:
  * enable dchp `systemctl start dhcpcd`
  * on boot start dchp `systemctl enable dhcpcd` do the same for ssh so i can stop doing everything on the terminal
  * enable dchp `systemctl start sshd`
  * on boot start dchp `systemctl enable sshd`
  * install fish shell
  * Add user [https://gist.github.com/kevinwright/6884737](https://gist.github.com/kevinwright/6884737) + SUDO
  * use ssh to get into my system from my laptop `cat >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys`
  * install some utils `htop`, `tmux`, `wget`, `git`, `go`, `fzf`, `inetutils`, `grc` `--needed base-devel`
  * install `vim-plug` `curl -fLo ~/.vim/autoload/plug.vim --create-dirs \ https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim`
  * install fisher `curl https://git.io/fisher --create-dirs -sLo ~/.config/fish/functions/fisher.fish`
  * install fzf binding for fisher
  * install bass compat layer: `fisher add edc/bass`
  * install grc to color: fisher add `oh-my-fish/plugin-grc`
  * install nvm: `fisher add jorgebucaran/fish-nvm`
  * install upto `fisher add markcial/upto`
  * install z `fisher add jethrokuan/z`
  * start getting dotfiles in order

