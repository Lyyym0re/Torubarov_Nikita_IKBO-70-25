# task 1
Вывести служебную информацию о пакете matplotlib (Python):  
```pip show matplotlib```  
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
```
array[1..2] of string: foo_versions =
    ["1.0.0", "1.1.0"];

array[1..2] of string: left_versions =
    ["not installed", "1.0.0"];

array[1..2] of string: right_versions =
    ["not installed", "1.0.0"];

array[1..3] of string: shared_versions =
    ["not installed", "1.0.0", "2.0.0"];

array[1..2] of string: target_versions =
    ["1.0.0", "2.0.0"];

array[1..1] of string: root_versions =
    ["1.0.0"];

var 1..1: root;
var 1..2: foo;
var 0..1: left;
var 0..1: right;
var 0..2: shared;
var 1..2: target;

constraint (root = 1) ->
    ((foo = 1 \/ foo = 2) /\ (target = 2));

constraint (foo = 2) ->
    ((left = 1) /\ (right = 1));

constraint (foo = 1) ->
    ((left = 0) /\ (right = 0));

constraint (left = 1) ->
    (shared >= 1);

constraint (right = 1) ->
    (shared = 1);

constraint ((left = 0) /\ (right = 0)) ->
    (shared = 0);

constraint (shared = 1) ->
    (target = 1);

solve satisfy;

output [
    "root = ", root_versions[fix(root)], "\n",
    "foo = ", foo_versions[fix(foo)], "\n",
    "left = ", left_versions[fix(left)+1], "\n",
    "right = ", right_versions[fix(right)+1], "\n",
    "shared = ", shared_versions[fix(shared)+1], "\n",
    "target = ", target_versions[fix(target)], "\n"
];
```
Ответ:  
```
root = 1.0.0
foo = 1.0.0
left = not installed
right = not installed
shared = not installed
target = 2.0.0
```
# task 7
Решение:  
```
packages = {
    "root": {
        "1.0.0": {
            "foo": ["1.0.0", "1.1.0"],
            "target": ["2.0.0"]
        }
    },

    "foo": {
        "1.0.0": {},
        "1.1.0": {
            "left": ["1.0.0"],
            "right": ["1.0.0"]
        }
    },

    "left": {
        "1.0.0": {
            "shared": ["1.0.0", "2.0.0"]
        }
    },

    "right": {
        "1.0.0": {
            "shared": ["1.0.0"]
        }
    },

    "shared": {
        "1.0.0": {
            "target": ["1.0.0"]
        },
        "2.0.0": {}
    },

    "target": {
        "1.0.0": {},
        "2.0.0": {}
    }
}


versions = {
    "root":   ["1.0.0"],
    "foo":    ["1.0.0", "1.1.0"],
    "left":   ["1.0.0"],
    "right":  ["1.0.0"],
    "shared": ["1.0.0", "2.0.0"],
    "target": ["1.0.0", "2.0.0"]
}


for package in packages:
    for version in packages[package]:

        package_number = versions[package].index(version) + 1

        dependencies = packages[package][version]

        for dependency in dependencies:

            allowed_versions = dependencies[dependency]

            conditions = []

            for allowed_version in allowed_versions:

                version_number = (
                    versions[dependency].index(allowed_version) + 1
                )

                conditions.append(
                    f"{dependency} = {version_number}"
                )

            condition = " \\/ ".join(conditions)

            print(
                f"constraint ({package} = {package_number}) "
                f"-> ({condition});"
            )
```
Ответ:  
```
constraint (root = 1) -> (foo = 1 \/ foo = 2);
constraint (root = 1) -> (target = 2);
constraint (foo = 2) -> (left = 1);
constraint (foo = 2) -> (right = 1);
constraint (left = 1) -> (shared = 1 \/ shared = 2);
constraint (right = 1) -> (shared = 1);
constraint (shared = 1) -> (target = 1);
```
