# task1
[root@localhost etc]# cut -d ":" -f 1 passwd | sort
# task2
[root@localhost ~]# cat /etc/protocols | awk '{print $2, $1}' | sort -k1,1nr | h
ead -n 5
# task3
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
