2024.08.06 20:32
Tags: #settings 

# BSPWM settings

OS планируется использовать на 2ух машинах с разным количеством мониторов.
То есть, необходим скрипт для определения количества мониторов, и, в зависсимости от этого, запуска разных конфигов.

Написал скрипт workspaces.sh:
```sh
#!/bin/bash

if type "xrandr"; then
  # Get the number of connected monitor
  num_connected=$(xrandr --query | grep " connected" | wc -l)

  # Log the number of connected monitors
  echo "$num_connected monitors are connected" >> /tmp/bspwm.log

  # Check the number of connected monitors and perform actions accordingly
  if [ "$num_connected" -eq 3 ]; then
    bspc monitor DP-1 -d 1 2 3
    bspc monitor HDMI-1 -d 4 5 6
    bspc monitor DVI-D-1 -d 7 8 9
  elif [ "$num_connected" -eq 2 ]; then
    # TODO change the names of monitors !!!
    bspc monitor DVI-D-1 -d 1 2 3 4 5
    bspc monitor HDMI-1 -d 6 7 8 9
  fi
else
  echo "executin default workspace" >> /tmp/bspwm.log

  bspc monitor primary -d 1 2 3 4 5 6 7
fi
```

Указываем bash в качестве интерпритатора

Сначала мы пытаемся найти путь для бинарника `xrandr`.
Если таковой имеется, то при помощи него же запрашиваем все устройства (или типа того), фильтруем их содержанию " connected", и выводим количество полученных строк.
После этого логируем результат и проверям его на точное совпадение.
В зависсимости от количества монитров применям соотвутствующую инструкцию. На данных момент актуален конфиг для 3ех мониторов, а так же для случая, когда `xrandr` отсутствует в системе.

Данный скрипт запускаем в главном файле конфигурации bspwm.
В данном случае это ~/.config/bspwm/bspwmrc

```
...
путь/до/скрипта.sh
...
```

Скорее всего скипту нужно будет выдать разрешение на запуск:
> chmod +x путь/до/скрипта.sh

Весь конфиг доступен в https://github.com/m4a1j9/bspwm-dotfiles по пути config/bspwm/

### Zero-Links
- [[00 Linux]]
- [[00 Config]]

### Links
- 