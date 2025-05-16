# LocalGit
My own local git server.

## Introduction
The main purpose of this project is to have a local git server located in a RaspberryPi 4B so I can access to my git repositories from anywhere at anytime.

## Why 

I could have simply used an online Git repository platform in order to upload the files so, why did I decide to create my own?

One of the reasons of this project is the limit of space in a repositry. I often design 3D objects and those files are usually heavy. See [size limits of GitHub](https://stackoverflow.com/questions/38768454/repository-size-limits-for-github-com).

## Tailscale

It has been stated that I want to be able to push and pull from anywhere even if I was in a different subnet so, how do I achieve this?

[Tailscale](https://tailscale.com) is a VPN service that streamlines connecting devices and services securely across different networks. I will be using the free plan to connect to my RaspberryPi.





## About the RaspberryPi

### Why this model

I could have used another version, the RaspberryPi 3 consumes less power than the RaspberryPi 4B and the RaspbeeyPi 5 is more powerful so, why did I go with the version 4?

For starters, I was worried about the electricity bill and the Pi 5 consumes almost twice the amount of the Pi 4. In order to lower the power consumption as much as I could, it runs an S.O. without desktop environment.

The main reason why I did not go with the Pi 3 is because of the ethernet speed. The port only has 100 Mbit of capacity and a 1 Gbit usb connector will not work, as the usb bandwidth is only 480 Mbit.
The Pi 4 solves this. The Pi 3B+ also solves this, however, I already had a Pi 4 from a previous project. [Pi 3 speed forum](https://forums.raspberrypi.com/viewtopic.php?t=160270).


### Storage limits

The Pi 4 runs on a nano SD card of 32 GB so I cannot store a lot in the Pi. The solution is having an external drive. The one I used is an internal one of 256 GB connected to the 3.0 USB port using an adaptor. 

When the Pi is rebooted, it looses then mount of the drive, so I had to edit the configuration file `/etc/fstab` adding this line:
`UUID=uuid_number /media/Disk auto rw,user,auto,nofail 0 2`.

`nofail` allows the boot sequence to continue even if the drive fails to mount.

### Final setup

The RaspberryPi is connected to a Switch through a RJ45 cable and to the power with its official charger. In addition to that, it also has a SSD disk coonected to the 3.0 USB port.

It does not have any display, keyboard or mouse cable since I can simply log in with another computer using ssh.


## Additional files

`upload.sh` is a shell script which simply adds all the new and modified files, makes a commit with the date as the message and does a push.


## Future intentions

I want to syncronize the content of my gits repositories when I turn on and power off one of my computers. Now I have to sign in in tailscale once a day when I do a push or a pull since it authenticates through ssh. Some of the ideas are using https with token or using Git Daemon (unsecure).





