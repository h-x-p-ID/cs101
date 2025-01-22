# Assignment #2: 语法练习



Updated 0126 GMT+8 Sep 24, 2024

2024 fall, Complied by 胡新璞，工学院



## 1.题目



### 263A. Beautiful Matrix

```
matrix = []
for _ in range(5):
	matrix.append(list(map(int, input().split())))
for i in range(5):
  	for j in range(5):
        if matrix[i][j] == 1:
			num = abs(2-i) + abs(2-j)
       	 	break
     	else:
       		continue
print(num)
```

 

### 1328A. Divisibility Problem

```
n = int(input())
for _ in range(n):
	a,b = map(int,input().split())
	if a % b == 0:
    	print(a % b)
  	else:
		print(b - a % b)
```



### 427A. Police Recruits

```
n = int(input())
lst = list(map(int, input().split()))
lst_crime = [0] * n
crime = 0
police = 0
for i in range(n):
	if lst[i] == -1:
     	if police == 0:
       		lst_crime[i] = 1
     	else:
       		police -= 1
   	else:
     	police += lst[i]
print(sum(lst_crime))
```





### 02808: 校门外的树

```
l,m = map(int,input().split())
tree = [1] * (l+1)
for _ in range(m):
    a,b = map(int,input().split())
    for i in range(a,b+1):
        tree[i] = 0
print(sum(tree))

```



### sy60: 水仙花数II

```
a,b = map(int,input().split())
res = ""
for i in range(a,b+1):
    a = int(str(i)[0])
    b = int(str(i)[1])
    c = int(str(i)[2])
    if i == a ** 3 + b ** 3 + c ** 3:
        res = res + str(i) + " "
if res == "":
    print("NO")
else:
    print(res[:-1])
```



### 01922: Ride to School

没做。



## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

 

这是第二周的作业，难度感觉比第一周确实高了一些，主要体现在数学层面的思考以及转化成代码时的思维，像第六题感觉就比较吓人所以暂时先没有提交这题。整体上，还是比较习惯用一些基本的操作，比如常规的输入多行数据、转化为数组等，很多题目用一些基本的操作比如if else等都还可以解决（暂时没有遇到超时的问题），之后会去看一下标准答案看看有没有什么更好的方法，顺便学习其中的语法知识。每日选做努力追赶进度中……