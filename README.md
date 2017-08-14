# Alx module for the Linux kernel with Wake-on-LAN support

**_Caveat emptor_**: this implementation of WoL is known to work on some machines and to be buggy on some others.

## Build and install

To build the module:
```
$ make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
```

To try it (last line enables WoL on magic packets, replace `eth0` with the name of your Ethernet interface):
```
# rmmod alx
# insmod ./alx.ko
# ethtool -s eth0 wol g
```

The commands above will not survive to a reboot. If this module does not kill your dog and you want to install it permanently then [DKMS](https://github.com/dell/dkms) is your friend.

## Authors
The code comes from the [alx module](https://github.com/torvalds/linux/tree/master/drivers/net/ethernet/atheros/alx) of the Linux kernel, and the old [WoL implementation](https://github.com/torvalds/linux/commit/bc2bebe8de8ed4ba6482c9cc370b0dd72ffe8cd2) (removed from the kernel in 2013) which is adapted here for v4.12. The authors of the specific parts are listed in the file headers and in the history of the [Linux repository](https://github.com/torvalds/linux).

## License
The code is licensed under [GPL 2.0](https://github.com/torvalds/linux/blob/master/COPYING).
