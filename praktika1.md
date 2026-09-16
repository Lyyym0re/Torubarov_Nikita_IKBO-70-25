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
