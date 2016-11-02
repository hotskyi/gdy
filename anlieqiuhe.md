### 对文件内容按列求和
在Shell中，我们可以用awk实现按列求和的功能，非常简单。看下面的例子：
* 简单的按列求和
```
[root@gdytest ~]# cat 456.txt 
123.52
125.54
126.36
[root@gdytest ~]# awk '{sum += $1};END {print sum}' 456.txt 
375.42
```
* 对符合某些条件的行，按列求和，比如对文件test中 第一列为aaa的行求和
```
[root@gdytest ~]# cat 123.txt 
aaa 123.52
bbb 125.54
aaa 123.52
aaa 123.52
ccc 126.36
[root@gdytest ~]# awk '/aaa/ {sum += $2};END {print sum}' 123.txt 
370.56
```
* 如果需求是：aaa的总和bbb的总和ccc的总和
```
[root@gdytest ~]# cat 123.txt 
aaa 123.52
bbb 125.54
aaa 123.52
aaa 123.52
ccc 126.36
[root@gdytest ~]# cat 123.txt | awk '{a[$1] += $2} END{for(i in a)print i,a[i]}'
aaa 370.56
bbb 125.54
ccc 126.36
```

