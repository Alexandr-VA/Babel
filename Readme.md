Описание
Ваша задача подключить Babel к проекту и настроить сборку с его использованием.

Установите Babel (npm install --save-dev @babel/core @babel/cli @babel/preset-env).

Установите CoreJS (npm install core-js@3).

Настройте скрипт запуска build для сборки с помощью npm. Для этого в секции scripts файла package.json пропишите:

{
    ...
    "scripts": {
        ...
        "build": "babel src -d dist"
        ...
    }
}
Создайте конфиг babel.config.json и пропишите @babel/preset-env:
{
  "presets": [
    [
      "@babel/preset-env",
      {
        "useBuiltIns": "entry",
        "corejs": "3.22"
      }
    ]
  ]
}
Создайте файл src/app.js со следующим содержимым:
const characters = [
  {name: 'мечник', health: 10},
  {name: 'маг', health: 100},
  {name: 'маг', health: 0},
  {name: 'лучник', health: 0},
];

const alive = characters.filter(item => item.health > 0);
Удостоверьтесь, что проект собирается, если в консоли запустить команду npm run build, и в каталоге dist формируется преобразованный Babel код.

Добавьте каталог dist в .gitignore.

