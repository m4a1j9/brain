2024.09.11 16:35
Tags: #1quest 

# EMSDK

### Установка (Arch linux)
1. установить пакет
> yay -S emsdk
2. прокинуть пути в PATH. Для fish shell инструкции таковы
> fish_add_path /usr/lib/emsdk
> fish_add_path /usr/lib/emsdk/upstream/emscripten
3. установить программу
> emsdk install latest
4. активировать программу
> emsdk activate

При проблемах 1 из опций помощи - посмотреть описание пакета AUR
### Zero-Links
- [[00 Config]]
- [[00 Linux]]

### Links
- [[Arch linux tips]]