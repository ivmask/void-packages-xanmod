## XBPS source packages including xanmod Kernel templates


Clone the `void-packages-xanmod` git repository and install the bootstrap packages:

```
$ git clone https://github.com/ivmask/void-packages-xanmod.git
$ cd void-packages-xanmod
$ ./xbps-src binary-bootstrap
```

Modify `etc/conf` to build packages marked as 'restricted'

```
$ echo XBPS_ALLOW_RESTRICTED=yes >> etc/conf
```

Build the desired kernel package by using:
```
$ ./xbps-src -f -jX linuxX.X-xanmod linuxX.X-xanmod-headers
```
# Compiling time will depend on how much CPU threads are being used, and obviously, CPU specs. You can modify the number of used threads by changing the ```-jX``` flag, replacing 'X' with the desired number.

Once built, the package will be available in `hostdir/binpkgs`. To install it:

```
# sudo xbps-install --repository hostdir/binpkgs linuxX.X-xanmod linuxX.X-xanmod-headers
```
To finish the installation and make sure grub boot entries are added, use the xbps-reconfigure command.

```
$ sudo xbps-reconfigure -f linuxX.X-xanmod
```
