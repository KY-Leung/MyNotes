Before we get started, we need to make sure that the Pi is updated. 

```
sudo apt-get update
```



```
sudo raspi-config
passwd
```

https://www.raspberrypi.org/forums/viewtopic.php?t=193620



An upgrade to the whole system isn"t needed but it is recommended:

- `sudo apt-get upgrade`



- `sudo apt-get install matchbox-keyboard`

Rebooting is recommended:

- `sudo reboot`



famine



`sudo shutdown -h now` (or `sudo halt`) 

> `-h` means halt the system `now` means do it straight away. You could also add number `10` to tell it to shut down in 10 minutes. You can even give a specific time `19:45` (in 24 hour format with a : colon). 

`sudo shutdown -r now` (or `sudo reboot`) 



# [How do I set or reset the Web interface Password?](https://discourse.pi-hole.net/t/how-do-i-set-or-reset-the-web-interface-password/1328)

pihole -a -p 



# [Pihole install error on a fresh Raspbian Stretch - non-root privileges](https://discourse.pi-hole.net/t/pihole-install-error-on-a-fresh-raspbian-stretch-non-root-privileges/7690)



curl -sSL [https://install.pi-hole.net](https://install.pi-hole.net/)| sudo bash 



```
["Kieran iPhone","Qing Yang iPhone","Qing Yang MBP","Nick MBP","Kai Yiu OnePlus","Hubert OnePLus","Zeng Hou MBP 1","Zeng Hou MBP 2","Wayne Laptop","Dhruv Pixel","Dhruv MBP","Lin Han iPhone","Lin Han Laptop","Arkar Galaxy","Josh","Josh MBP","Germaine MBP"]

["1c:5c:f2:d0:19:72","b8:53:ac:21:e7:61","8c:85:90:6f:72:b9","a4:se:60:d7:72:07","c0:ee:fb:f7:5f:46","94:65:2d:6e:54:db","78:4f:43:81:41:17","8c:85:90:3b:77:c0","e4:a4:71:64:c2:c9","10:f1:f2:87:ae:9c","02:0f:b5:2e:49:c8","c0:d0:12:b2:df:cb","4c:32:75:9b:77:33","30:07:4d:2d:0a:91","78:4f:43:3e:5e:b4","8c:85:90:26:79:53","8c:85:90:2d:b4:49"]
```

