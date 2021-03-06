# Useful Linux Commands

Index of Contents:

* [awk](#awk)
* [chroot](#chroot)
* [date](#date)
* [dialog](#dialog)
* [du](#du)
* [expac](#expac)
* [fc-list](#fc-list)
* [file](#file)
* [grep](#grep)
* [htop](#htop)
* [iotop](#iotop)
* [ip](#ip)
* [ncdu](#ncdu)
* [nethogs](#nethogs)
* [nl](#nl)
* [pidof](#pidof)
* [pkill](#pkill)
* [powertop](#powertop)
* [sed](#sed)
* [setxkbmap](#setxkbmap)
* [tee](#tee)
* [tree](#tree)
* [xargs](#xargs)
* [xev](#xev)
* [yes](#yes)


## awk

Select particular columns and print out;
```bash
lsblk | awk '{print $1,$4}'
# sda 8GB
```

## chroot

Opens a new TTY on given root directory.

## date

Get unix timestamp:

```
date +%s
```

Get date & time nicely formatted;

```
date '+%d %h %H:%M'
# 22 Jun 01:42
```

## dialog
You can create UI dialogs with it on command-line easily. For example;

```bash
  usernameDialog () {
      username=$(dialog --stdout \
                        --title "Creating Users" \
                        --backtitle "Happy Hacking Linux" \
                        --ok-label "Done" \
                        --nocancel \
                        --inputbox "Choose your username" 8 50)
  }
```

## du
Checks size of a folder.

  ```bash
  du -sh /
  ```

## expac
Data extraction tool for ALPM (Arch Linux Package Management).

To list packages by their size;
```bash
  expac "%n %m" -l'\n' -Q $(pacman -Qq) | sort -rhk 2 | less
```

```
  yes | pacman -S yolo
```

## fc-list
Lists fonts available in the system.

```bash
fc-list | grep Monaco
```

## file

Returns file info. It's especially useful on images;

```bash
file logo.png
# PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
```

## grep

Match patterns with text, print not matched;

```bash
grep -oFf patterns.txt text.txt | grep -vFf - patterns.txt
```

## htop

Interactive process viewer. Useful keybindings:

* `/` Search
* `\` Filter
* `,` Choose the sorting criteria
* `k` Send kill signal to selected process
* `u` Filter results by user
* `t` Open/close tree mode
* `-` or `+` Collapse/uncollapse process trees
* `H` Turn off displaying threads

## iotop

Sorts processes by disk writes, and show how much and how frequently programs are writing to the disk.

## ip

List network interfaces in the system:

```bash
ip link show
```

Manage routing tables:

```
ip r
```
## ncdu
Disk usage analyzer with CLI UI with ncurses.

## nethogs

htop for network. lists processes by their network traffic.

## nl
Adds line numbers to beginning of each line.

```bash
cat foobar.txt | nl
```

## pidof

Find process id of a running program:

```
pidof nginx
```

It might return multiple pids (e.g nginx have worker processes). Specify `-s` parameter to get only one pid:

```
pidof -s nginx
```

## pkill

Kill a process partially matching given pattern;

```
pkill -f pattern
```

## powertop
Lists processes by their energy consume.

## sed

Display nth line in a large file:

```bash
sed '26577519q;d'
```

Replace nth line in a large file:

```bash
sed -i '26577519s/ &#3;/ /' content.rdf.u8
```

Uncomment matching line:

```bash
sed -i -e '/^#en_US/s/^#//' /etc/locale.
```

Slugify a string:

```bash
sed -e 's/[^[:alnum:]]/-/g' | tr -s '-' | tr A-Z a-z
```

## setxkbmap

Sets the keyboard layout:

```
setxkbmap tr -variant alt -option lv3:ralt
```

## tee

It's used for splitting the output of a program so we can both display it and also save it.

For example, add a new entry to hosts file;

```
echo "127.0.0.1 foobar" | sudo tee -a /etc/hosts
```

## tree

Lists contents of a directory in tree-like format.

```
tree
```

Show hidden files:

```
tree -a
```

Show only directories:

```
tree -d
```

## xargs

Build an execute commands from standard input

```bash
xargs -n 1 curl < download.txt
```

## xev

Creates a window and lets you see the keyboard events. Useful when you modify keybindings.


## yes
Approve all confirmations

```bash
  yes | pacman -S yolo
```
