
Some notes about bash stuff

you can use &&, but if you need run a command after other, and not matters it the first is correctly executed or not, yu can use ;

```bash
sudo pacman -Syu && echo "done"

#vs

sudo pacman -Syu; echo "done"
```

### one trick for pacman, but sure can work on others package managers

You can now where is a package with "whereis" command

```
~$: whereis netstat

> netstat: /usr/bin/netstat /usr/share/man/man8/netstat.8.gz


```

but you can not know from where this package cames from (what is the program which instale it).

so you can use:

```
~$: sudo pacman -Qo /usr/bin/netstat

> /usr/bin/netstat is owned by net-tools <version here>
```

but in addition you can do this for pkg which you DON'T HAVE.

```
sudo pacman -F netstat

```

---

transform text at images in "real text" (transcibe)

```
sudo pacman -Ss tesseract
```

use this program for ral the iamge

```
tesseract textimage.jpg text
```
---

use "yes" for autoconfirm

```
sudo pacman -Ss yes
```

All not package managers have the option for skip confirmation, can be needed on scripts, pipes... etc





[video at yt](youtube.com/watch?v=3lRrEEwTlyc)
