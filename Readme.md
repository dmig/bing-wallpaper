# Linux Bing Wallpaper changer

Yet another set of scripts for modern Linux ditro powered by `systemd`. Inspired by code of https://github.com/whizzzkid/bing-wallpapers-for-linux and
https://github.com/marguerite/linux-bing-wallpaper.
Actually `update-bing-wallpaper` is cleaned up and simplified fork of https://github.com/whizzzkid/bing-wallpapers-for-linux/bingwallpaper, so my acknoledgment to its author.

# Reqirements
- `wget` -- mot likely you have it installed
- `notify-send` -- to show notifications (`sudo apt install libnotify-bin`) or `notify-send.sh` -- more powerful version of `notify-send` (https://github.com/vlevit/notify-send.sh)

# Installation
```shell
wget https://github.com/marguerite/linux-bing-wallpaper/archive/master.zip
unzip master.zip
cp -r bing-wallpaper-master/bin ~
chmod +x ~/bin/update-bing-wallpaper
```
Edit this file `~/bin/update-bing-wallpaper` to adjust wallpaper size/save path.

If you want wallpaper to be updated automatically (around 9:00, or soon after your login)
```shell
cp -r bing-wallpaper-master/.config ~
systemctl --user daemon-reload
systemctl --user enable bing-wallpaper.timer
systemctl --user start bing-wallpaper.timer
```
And finally, cleanup
```shell
rm master.zip && rm -rf bing-wallpaper-master
```

# Usage
- manually:
```shell
update-bing-wallpaper
```
this command will grab latest wallpaper (updated daily, won't download twice)
- or install `systemd` timer and enjoy

To disable timer execute
```shell
systemctl --user stop bing-wallpaper.timer
```

