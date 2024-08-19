2024.08.19 22:28
Tags: #2done 

# OpenVPN config for linux

I use Arch btw


Воспользуемся aur пакетом openvpn3
> yay -S openvpn3

Так же нам потребуется конфиг от организации
Для унификации и удобста использования разместим его в /etc/openvpn/название

Начать сессию можно командой
> openvpn3 session-start --config /etc/openvpn/nntc.ovpn

Остановить сессию можно следующим способом:
1. Просмотреть список активных сессий
   > openvpn3 sessions-list
2. Скопировать путь и указать его для остановки
   > openvpn3 session-manage --session-path /net/openvpn/v3/sessions/id_сессии --disconnect
### Zero-Links
- [[00 Config]]
- [[00 Work]]

### Links
- 