2024.08.04 22:01
Tags: #settings #work #code

# Debug in nvim via nvim-dap

На текущий момент репозиторий зранится в https://github.com/m4a1j9/nvim

В качестве адптера будем использовать `nvim-dap-vscode-js`

На текущий момент в качестве браузера используем AUR yandex-brouser

В конфигурации языкового адаптера важно указать путь до исполняемого файла. В нашем случае это:
`runtimeExecutable = "/usr/bin/yandex-browser-stable",`
Путь можно узнать командой `yay -Ql yandex-browser | grep stable`
Это нужно отлько для запуска нового процесса

Для интеграции существующего делаем следующее.
Браузер должен быть запущен с определенным портом дебаггера:
`yandex-browser-stable --remote-debugging-port=9222`
который так же должен быть указан в конфиге языкового адаптера:
`port = 9222`

### Zero-Links
- [[00 IDE]]
- [[00 Linux]]
- [[00 Config]]

### Links
- [[]]
