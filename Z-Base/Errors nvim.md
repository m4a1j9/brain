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
### Zero-Links
- [[00 Errors]]
- [[00 IDE]]

### Links
- [[Debug in nvim]]