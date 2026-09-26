# task 1
Вывести служебную информацию о пакете matplotlib (Python):  
``` python -m pip show matplotlib ```  
Служебная информация о пакете matplotlib хранится в файле METADATA каталога:matplotlib-3.10.8.dist-info  
Поле Metadata-Version означает версию стандарта, по которому записаны метаданные пакета. Поле Name содержит название пакета,
Version — его версию, Summary — краткое описание, Author - автор.
Также файл содержит сведения о лицензии и ссылки на ресурсы проекта.  
Получить пакет без менеджера пакетов:  
```git clone https://github.com/matplotlib/matplotlib.git```
# task 2
Вывести служебную информацию о пакете express (JavaScript):  
```cat package/package.json```  
Основные элементы содержимого файла со служебной информацией из пакета: name — имя пакета, description — краткое описание, version — версия пакета, 
author - автор пакета, contributors - составители пакета, license — лицензия, repository — адрес репозитория исходного кода, homepage - страница пакета,
dependencies — зависимости, необходимые для работы пакета, devDependencies — зависимости, которые нужны только при разработке самого Express, 
engines — требования к среде выполнения, например к версии Node.js, scripts — команды проекта, например запуск тестов.  
Получить пакет без менеджера пакетов:  
```git clone https://github.com/expressjs/express.git```
# task 3
Зависимости matplotlib:
```
digraph matplotlib{
        "matplotlib" -> "contourpy";
        "matplotlib" -> "cycler";
        "matplotlib" -> "fonttools";
        "matplotlib" -> "kiwisolver";
        "matplotlib" -> "numpy";
        "matplotlib" -> "packaging";
        "matplotlib" -> "pillow";
        "matplotlib" -> "pyparsing";
        "matplotlib" -> "python-dateutil";
}
```
Зависимости express:
```
digraph express{
        "express" -> "accepts";
        "express" -> "body-parser";
        "express" -> "content-disposition";
        "express" -> "content-type";
        "express" -> "cookie";
        "express" -> "cookie-signature";
        "express" -> "debug";
        "express" -> "depd";
        "express" -> "encodeurl";
        "express" -> "escape-html";
        "express" -> "etag";
        "express" -> "finalhandler";
        "express" -> "fresh";
        "express" -> "http-errors";
        "express" -> "merge-descriptors";
        "express" -> "mime-types";
        "express" -> "on-finished";
        "express" -> "once";
        "express" -> "parseurl";
        "express" -> "proxy-addr";
        "express" -> "qs";
        "express" -> "range-parser";
        "express" -> "router";
        "express" -> "send";
        "express" -> "serve-static";
        "express" -> "statuses";
        "express" -> "type-is";
        "express" -> "vary";
}
```
Сформировать png зависимостей matplotlib:  
```dot -Tpng matplotlib.dot -o matplotlib.png```  
Сформировать png зависимостей express:  
```dot -Tpng express.dot -o express.png```
# task 4
Решение:  
```
include "alldifferent.mzn";

array[1..6] of var 0..9: d;

constraint d[1] + d[2] + d[3] = d[4] + d[5] + d[6];

constraint all_different(d);

solve minimize d[1] + d[2] + d[3];

output[
  "Ticket: ", show(d[1]), show(d[2]), show(d[3]),
  show(d[4]), show(d[5]), show(d[6]), "\nSum: ",
  show(d[1] + d[2] + d[3])
];
```
Ответ:  
```
Ticket: 620431
Sum: 8
```
# task 5
Решение:  
```
array[1..6] of string: menu_versions =
  ["1.0.0", "1.1.0", "1.2.0", "1.3.0", "1.4.0", "1.5.0"];

array[1..5] of string: dropdown_versions = 
  ["1.8.0", "2.0.0", "2.1.0", "2.2.0", "2.3.0"];

array[1..2] of string: icons_versions = ["1.0.0", "2.0.0"];

var 1..6: menu;
var 1..5: dropdown;
var 1..2: icons;

constraint icons = 1;

constraint menu = 1 -> dropdown = 1;

constraint menu >= 2 -> dropdown >= 2;

constraint dropdown >= 2 -> icons = 2;

solve satisfy;

output[
  "menu = ", menu_versions[fix(menu)], "\n",
  "dropdown = ", dropdown_versions[fix(dropdown)], "\n",
  "icons = ", icons_versions[fix(icons)], "\n"
];
```
Ответ:  
```
menu = 1.0.0
dropdown = 1.8.0
icons = 1.0.0
```
# task 6
