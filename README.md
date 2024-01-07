# bri
Simplest screen brightness control.


### Installation.

You need to be able to write into the file `/sys/class/backlight/*/brightness`.
To make the change persistent, you can add a udev rule:

```
# Allow screen brightness control for everyone.
$ > /etc/udev/rules.d/80-backlight.rules \
    echo 'ACTION=="add", SUBSYSTEM=="backlight", KERNEL=="intel_backlight", RUN+="/bin/chmod a+w /sys/class/backlight/%k/brightness"'

# Enact the rule.
$ sudo udevadm trigger --verbose --action=add /sys/class/backlight/intel_backlight/
```


### Usage.

```
$ bri +N  # Increase brightness by 'N'.
$ bri -N  # Decrease brightness by 'N'.
```
