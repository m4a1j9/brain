2024.08.05 02:53
Tags: #work 

# Solutions for errors in nvim

- nvim treesitter Invalid node type "string_content"
Обновить парсеры `TSUpdate`
Убедиться, что парсер только 1.
`:echo nvim_get_runtime_file('parser', v:true)`
Если нет, то удалить тот, что не находится в папке nvim-treesitter

- nvim-dap could not find any debuggable targer
Запустить браузер с явно указанным портом для дебаггера
`yandex-browser-stabel --remote-debugging-port=9222`

- Missing "neovim" npm (or yarn, pnpm) package.
Установить neovim:
`npm i -g neovim`
Проблема может не решится, если в системе используется nvm и nodejs, установленный через pacman. В этом случае nvm в приоритете, поэтому нужно удалить nodejs и npm в pacman:
`sudo pacman -R nodejs npm`
Если от пакета зависят другие пакеты, то удаляем все рекурсивно:
`sudo pacman -Rsc nodejs npm`
### Zero-Links
- [[00 Errors]]
- [[00 IDE]]

### Links
- [[Debug in nvim]]