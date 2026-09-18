# task1
```cut -d ":" -f 1 passwd | sort```
# task2
```cat /etc/protocols | awk '{print $2, $1}' | sort -k1,1nr | head -n 5```
# task3
```
#!/bin/sh

string="$1"
length=${#string}
echo -n "+"
i=0
while [ $i -lt $((length + 2)) ]
do
        echo -n "-"
        i=$((i + 1))
done
echo "+"

echo "| $string |"

echo -n "+"

i=0
while [ $i -lt $((length + 2)) ]
do
        echo -n "-"
        i=$((i + 1))
done
echo "+"
```  
# task4
```
#!/bin/sh

file="$1"
sed '/\/\*/,/\*\//d' "$file" |
grep -oE '[A-Za-z_][A-Za-z0-9_]*' | sort -u | xargs
```
# task5
```
#!/bin/sh

file="$1"
if [ -f "$file" ]; then
        chmod +x "$file"
        cp "$file" /usr/local/bin
fi
```
# task6
```
for file in *.py *.c *.js
do
        [ -f "$file" ] || continue
 
        line=$(head -n 1 "$file")
        line=$(echo "$line" | sed 's/^[[:space:]]*//')
 
        case "$file" in
        *.py)
                case "$line" in
                "#"*)
                        echo "$file: комментарий есть"
                        ;;
                *)
                        echo "$file: комментария нет"
                        ;;
                esac
                ;;
 
        *.c|*.js)
                case "$line" in
                "//"*|"/*"*)
                        echo "$file: комментарий есть"
                        ;;
                *)
                        echo "$file: комментария нет"
                        ;;
                esac
                ;;
        esac
done
```
# task7
```
#!/bin/sh
 
path="$1"
if [ -z "$path" ]
then
        echo "Укажите путь"
        exit 1
fi
 
list="/tmp/files.txt"
 
find "$path" -type f > "$list"
 
n=0
 
while IFS= read -r file1
do
        n=$((n+1))
        m=0
 
        while IFS= read -r file2
        do
                m=$((m+1))
 
                if [ "$m" -le "$n" ]
                then
                        continue
                fi
 
                if cmp -s "$file1" "$file2"
                then
                        echo "Дубликаты: $file1 и $file2"
                fi
 
        done < "$list"
 
done < "$list"
 
rm "$list"
```
# task8
```
#!/bin/sh
 
dir=$1
ext=$2
if [ ! -d "$dir" ]
then
        echo "Директории $dir не существует"
        exit 1
fi
 
tar -cf archive.tar "$dir"/*."$ext"
 
echo "done"
```
# task9
```
#!/bin/sh
 
fileinput="$1"
fileoutput="$2"
 
if ! [ -f "$fileinput" ]
then
        echo "Проверьте существует ли файл"
        exit 1
fi
 
sed 's/    /\t/' "$fileinput" > "$fileoutput"
```
# task10
```
#!/bin/sh
 
dir="$1"
 
if ! [ -d "$dir" ]
then
        echo "Директортия не найдена"
        exit 1
fi
 
for file in "$dir"/*
do
        if [ -f "$file" ] && [ ! -s "$file" ]
        then
                echo "$file"
        fi
done
```
