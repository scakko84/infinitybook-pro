# TUXEDO Computers InfinityBook Pro 14 - Gen 6 post-install troubleshooting guide

## Screen flickering

In order to solve screen flickering on older kernels edit the Grub defaults

```console
$ sudo vi /etc/default/grub
```

and add `i915.enable_psr=0` to `GRUB_CMDLINE_LINUX_DEFAULT`

Then update grub

```console
$ sudo update-grub
```

and reboot to the updated kernel.

## Wi-Fi random disconnections

In order to solve random Wi-Fi disconnections edit the NetworkManager Wi-Fi powersave configuration

```console
$ sudo vi /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

changing `wifi.powersave = 3` to `wifi.powersave = 2`.

## Apple AirPods pairing fails

In order to connect the Apple AirPods edit the bluetooth system configuration

```console
$ sudo vi /etc/bluetooth/main.conf
```

changing `ControllerMode = dual` to `ControllerMode = bredr`.

Restart the bluetooth service

```console
$ sudo systemctl restart bluetooth
```

And pair the Apple AirPods again.
