2024.09.23 02:27
Tags: #

# Arch liux issues

### yay error while loading shared libraries
Error message:
>yay: error while loading shared libraries: libalpm.so.13: cannot open shared object file: No such file or directory

The solution:
reinstall yay
>pacman -S --needed git base-devel
>git clone https://aur.archlinux.org/yay.git
>cd yay/
>makepkg -si

### Pacman  error failed retrieving file
Just update entire system
> sudo pacman -Syu

### Zero-Links
- [[00 Linux]]

### Links
- [[Arch linux tips]]