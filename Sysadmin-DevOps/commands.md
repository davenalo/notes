There are some commands which may do the "same" things. It is,  can return the same value but doing a different process.

```
pacman -Qq | wc -l
# word count; lines

pacman -Qq | nl
#number of lines

#And maybe you can do it with "count" command.

```

There are some utilities that can have very similar functions:

parted,
fdisk cfdisk sfdisk
gdisk cgdisk sgdisk

---

```
grep -c ".*" .bashrc
sed -n "$=" .bashrc
awk "END{print NR}" .bashrc
cat -n .bashrc | tail -n 1 | cut -f 1
```

whereis, which,
---


There are too commands which are different, make similar things, but is better in every situation use one of them.

adduser - useradd
ip - ifconfig

https://andys.org.uk/bits/2010/02/24/iproute2-life-after-ifconfig/

https://dougvitale.wordpress.com/2011/12/21/deprecated-linux-networking-commands-and-their-replacements/

https://inai.de/2008/02/19?range=2008/02/19

--

Please keep in mind that most net-tools programs are obsolete now:

program   obsoleted by
arp       ip neigh
ifconfig  ip addr
ipmaddr   ip maddr
iptunnel  ip tunnel
route     ip route
nameif    ifrename
mii-tool  ethtool
 

---
Sudoers file

```
visudo

# the % symbols inside the file stands for "group"
```

in this file will be the storage of the group permissions

----------

sort command 

sort -r -> reverse order
sort -f -> insensitive capitalization
sort -n -> sort numerically

-----

lsof -> open files list
nslookup - Name Server Lookup (DNS Information)

-----

id -> information about users
who -> who has an open session
w -> same as who but with more info
uname -a -> info about the system
---
du
free
df -> disk free
```
df -h
```
uptime
last -> lasts boots of the system

--

tar -xvf tar-file

---

```
cut -c1-2 file
#corta la por columnas, hasta dos caracteres
```

----

watch -> returns every 2 seconds the output from an target command

---
eval

---

history

```
!42
```

---

dd

```
dd inputfile = /dev... outputfile = /dev...
```
---

free -> memory on the system

----

passwd -> change your password

passwd -e user -> if runned as root, expires the password of the user and obligate them to choose another one

----

man
info
tldr

apropos -> used to search a command which you don't know the name.

```
apropos copy


#Display a list of "copy" related commands
```
---

mount

---

head
tail

---







