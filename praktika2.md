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
