2024.08.06 20:45
Tags: #settings 

# Polybar settings

OS планируется использовать на 2ух машинах с разным количеством мониторов.
То есть, необходим скрипт для определения количества мониторов, и, в зависсимости от этого, запуска разных конфигов.

Написал скрипт universal_launch.sh:
```sh
#!/bin/bash

echo "universal_launch" >> /tmp/polybar1.log

if type "xrandr"; then
  monitors_list=$(xrandr --query | grep " connected" | cut -d" " -f1)

  echo "available monitors: $monitors_list" >> /tmp/polybar1.log

  for m in $monitors_list; do
    echo "launch polybar for $m monitor" >> /tmp/polybar1.log

    MONITOR=$m polybar --reload single &
  done
else
  echo "xrandr is not detected" >> /tmp/polybar1.log

  polybar --reload single
fi
```

Указываем bash в качестве интерпритатора

Логируем запуск скрипта
Пытаемся найти путь для бинарника `xrandr`.
Если таковой имеется, то при помощи него же запрашиваем все устройства (или типа того), фильтруем по наличию " connected" и обрезаем весь текст, кроме названия монитора и результат засовываем в переменную (или это функция, хз).
Снова логируем.
Потом проходимя по списку мониторов, логируем, и для каждого вызываем polybar с явно установленной переменной окружения MONITOR. В самом конфиге значени ключа `monitor` должно быть установлено на переданную переменную:
```ini
...
monitor = ${env:MONITOR:}
...
```

Данный скрипт запускаем в главном файле конфигурации polybar.
В данном случае это ~/.config/polybar/launch.sh

```
...
путь/до/скрипта.sh 2>> /tmp/polybar1.log
...
```

Так же выводим результат запуска в логи.

Скорее всего скипту нужно будет выдать разрешение на запуск:
> chmod +x путь/до/скрипта.sh


Весь конфиг доступен в https://github.com/m4a1j9/bspwm-dotfiles по пути config/polybar/
### Zero-Links
- [[00 Linux]]
- [[00 Config]]

### Links
- 