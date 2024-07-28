2024.04.20 15:33
Tags: #work #lesson

# Настойка NX монорепозитория

## Базовый монорепозиторий

Развёртывание и настройка стандартного монорепозитория на основе туториала: https://nx.dev/getting-started/tutorials/react-monorepo-tutorial

Основной стек:
- React
- Vite

Создать монорепу по стандартному шаблону:
`npx create-nx-workspace@latest ${название монорепы} --preset=react-monorepo

Запуск какого-либо из проектов:
`nx ${название проекта} react-store

Генерация нового приложения внутри монорепы:
`nx g @nx/react:app ${название приложения} --directory=${расположение приложения относительно корня проекта, например: apps/app2} --bundler=vite

Генерация дополнительных общих библиотек:
`nx g @nx/react:library ${название библиотеки} --directory=${расположение приложения относительно корня проекта, например: libs/lib2} --unitTestRunner=none --bundler=none

При необходимости можно указывать флаги с дополнительными параметрами проекта:
- --bundler=vite
- --unitTestRunner=vitest

При указании --bundler=none проект будет считаться модульным (без необходимости сборки)

Генерация компонентов:
`nx g @nx/react:component ${название компонента} --project=${название проекта, в котором будет создан компонент} --directory="${расположение компонента, например: libs/${название библиотеки}/src/lib/${название компонента}}"

Визуализация структуры проекта в виде графа:
`nx graph

## Разработка модульной федерации.

За основу взят туториал: https://nx.dev/concepts/module-federation/module-federation-and-nx

Стоит учесть, что хосты и ремоуты разворачиваются при помощи webpack.
### Типы приложений
#### Host
Верхняя обёртка, определяющая, на каком домене будет развернуто приложение. Состоит из ремоутов или модулей.
#### Remote
Основные блоки, из которых собирается приложение. Должны иметь фиксированный адрес. Могут состоять из модулей.
#### Federated Module
Небольшие блоки, широко используемые в разных ремоутах и хостах. Должны иметь фиксированный адрес.


Генерация хост-приложения:
`nx g @nx/react:host ${название хоста} --remotes=${название ремоута, название ремоута, название ремоута}

Можно не указывать ремоуты стразу, а прописать связь с хостом позже при их отдельной генерации:
`nx g @nx/react:remote ${название ремоута} --host=${название хоста}

Запуск хоста:
`nx serve ${название хоста} --open

Так же можно сразу запустить ремоуты:
`nx serve ${название хоста} --open --devRemotes="${название ремоута,название ремоута}"

Что бы указать зависимость хоста от ремоутов в контексте развертывания приложения, нужно указать ключ implicitDependencies в project.json текущего хоста:
```json
"implicitDependencies": ["${название ремоута}", "${название ремоута}", "${название ремоута}"],
```

Пример расширения конфига webpack, основанный на LicenseWebpackPlugin:
```ts
import { withModuleFederation } from '@nx/angular/module-federation';
import config from './module-federation.config';
import { LicenseWebpackPlugin } from 'license-webpack-plugin';
import { resolve } from 'path';

export default async function (wco) {
  const wmf = await withModuleFederation(config);
  return wmf({
    ...wco,
    plugins: [
      ...(wco.plugins ?? []),
      new LicenseWebpackPlugin({
        stats: {
          warnings: false,
          errors: false,
	    },
	    perChunkOutput: false,
	    outputFilename: '3rdpartylicenses.txt',
	    skipChildCompilers: true,
	    modulesDirectories: [resolve(__dirname, '../../node_modules')],
	  }),
	],
  });
}
```

Главный конфиг для соединения хоста и ремоутов - apps/host/module-federation.config.ts. Названия ремоутов должны соответствовать значению ключа name в настройках самих ремоутов.

## Полезные команды

Удалить дирректорию
`nx g rm ${назване дирректории}

### Zero-Links
- [[00 JS]]
- [[00 Work]]

### Links
- [[iifa-monorepo]]