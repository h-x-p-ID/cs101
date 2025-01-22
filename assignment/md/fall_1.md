# assignment 1



Updated 0126 GMT+8 Sep 24, 2024

2024 fall, Complied by 胡新璞，工学院



## 1.题目



#### 02733: 判断闰年

```
a = int(input())
if a % 4 == 0 and a % 100 != 0 or a % 400 == 0:
    print("Y")
else:
    print("N")
```



#### 02750: 鸡兔同笼

```
k = int(input())
if k % 2 != 0:
    print("0 0")
else:
    b = k // 2
    if k % 4 == 0:
        a = k // 4
    else:
        a = k // 4 + 1
    print(a,b)
```



#### 50A. Domino piling 2min

```
a,b = map(int,input().split())
print(a * b // 2)
```



#### 1A. Theatre Square

```
n,m,a = map(int,input().split())
if n % a == 0:
    nn = n // a
else:
    nn = n // a + 1
if m % a == 0:
    mm = m // a
else:
    mm = m // a + 1
print(nn * mm)
```



####  112A. Petya and Strings

```
def zh(a):
    b = ""
    for i in a:
        if ord(i) >= 65 and ord(i) <= 90:
            b += chr(ord(i) + 32)
        else:
            b += i
    return b

mm = input()
nn = input()
m = zh(mm)
n = zh(nn)
k = 0

for j in range(len(m)):
    if ord(m[j]) == ord(n[j]):
        continue
    elif ord(m[j]) > ord(n[j]):
        k += 1
        break
    else:
        k -= 1
        break

if k == 0:
    print(0)
elif k > 0:
    print(1)
else:
    print(-1)
```



#### 231A. Team

```
n = int(input())
sum = 0
for _ in range(n):
    a,b,c = map(int,input().split())
    if a + b + c >= 2:
        sum += 1
    else:
        continue
print(sum)
```



## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

 

这段时间花在代码上的时间不是很多，题目都是零碎时间敲的，拖到今天才交。我自己本身可能略有一点Python语言的基础（但也没有很多），况且两年没动了也快忘得差不多了，第一次作业基本是康复训练，练习一些基本的语法，题目本身也不需要什么复杂的代码设计。目前正在追赶每日选做的进度，国庆假期会投入较多的时间学习。
