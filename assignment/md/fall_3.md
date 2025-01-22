# Assign #3: Oct Mock Exam暨选做题目满百



Updated 1537 GMT+8 Oct 10, 2024

2024 fall, Complied by 胡新璞，工学院



## 1.题目



### E28674:《黑神话：悟空》之加密

http://cs101.openjudge.cn/practice/28674/

代码

```
k = int(input())
s = input()
ss = ""
kk = k % 26
for i in range(len(s)):
    if ord(s[i]) >= 65 and ord(s[i]) <= 90:
        if ord(s[i]) - kk < 65:
            ss = ss + chr(ord(s[i]) - kk + 26)
        else:
            ss = ss + chr(ord(s[i]) - kk)
    else:
        if ord(s[i]) - kk < 97:
            ss = ss + chr(ord(s[i]) - kk + 26)
        else:
            ss = ss + chr(ord(s[i]) - kk)
print(ss)
```

 

### E28691: 字符串中的整数求和

http://cs101.openjudge.cn/practice/28674/

代码

```
a = input()
b = int(a[0:2])
c = int(a[4:6])
print(c+b)
```



### M28664: 验证身份证号

http://cs101.openjudge.cn/practice/28664/

代码

```
dicta = {0:7,1:9,2:10,3:5,4:8,5:4,6:2,7:1,8:6,9:3,10:7,11:9,12:10,13:5,14:8,15:4,16:2}
dictb = {0:1,1:0,2:"X",3:9,4:8,5:7,6:6,7:5,8:4,9:3,10:2}
n = int(input())
for _ in range(n):
    num = 0
    sfz = str(input())
    for i in range(0,17):
        num = num + int(sfz[i]) * dicta[i]
    res = dictb[num % 11]
    if str(res) == sfz[17]:
        print("YES")
    else:
        print("NO")
```



### M28678: 角谷猜想

http://cs101.openjudge.cn/practice/28678/

代码

```
num = int(input())
while num > 1:
    if num % 2 == 1:
        print(str(num)+"*3+1="+str(num * 3 + 1))
        num = num * 3 + 1
    else:
        print(str(num)+"/2="+str(num//2))
        num = num // 2
print("End")
```



### M28700: 罗马数字与整数的转换

http://cs101.openjudge.cn/practice/28700/

思路：

忘记用字典了，写了个答辩一样复杂的if and else出来。字典的写法跟题解差不多，这里还是交我一开始的代码了。

代码

```
num = str(input())
if ord(num[0]) >= 65 and ord(num[0]) <=90:
    num_ = 0
    i = len(num) - 1
    while i >= 0:
        if num[i] == "I":
            num_ += 1
            i -= 1
        elif num[i] == "V":
            if i > 0 and num[i-1] == "I":
                num_ += 4
                i -= 2
            else:
                num_ += 5
                i -= 1
        elif num[i] == "X":
            if i > 0 and num[i-1] == "I":
                num_ += 9
                i -= 2
            else:
                num_ += 10
                i -= 1
        elif num[i] == "L":
            if i > 0 and num[i-1] == "X":
                num_ += 40
                i -= 2
            else:
                num_ += 50
                i -= 1
        elif num[i] == "C":
            if i > 0 and num[i-1] == "X":
                num_ += 90
                i -= 2
            else:
                num_ += 100
                i -= 1
        elif num[i] == "D":
            if i > 0 and num[i-1] == "C":
                num_ += 400
                i -= 2
            else:
                num_ += 500
                i -= 1
        elif num[i] == "M":
            if i > 0 and num[i-1] == "C":
                num_ += 900
                i -= 2
            else:
                num_ += 1000
                i -= 1
else:
    num = int(num)
    num_ = ""
    while num > 0:
        if num >= 1000:
            num_ += "M"
            num -= 1000
        elif num >= 900:
            num_ += "CM"
            num -= 900
        elif num >= 500:
            num_ += "D"
            num -= 500
        elif num >= 400:
            num_ += "CD"
            num -= 400
        elif num >= 100:
            num_ += "C"
            num -= 100
        elif num >= 90:
            num_ += "XC"
            num -= 90
        elif num >= 50:
            num_ += "L"
            num -= 50
        elif num >= 40:
            num_ += "XL"
            num -= 40
        elif num >= 10:
            num_ += "X"
            num -= 10
        elif num >= 9:
            num_ += "IX"
            num -= 9
        elif num >= 5:
            num_ += "V"
            num -= 5
        elif num >= 4:
            num_ += "IV"
            num -= 4
        else:
            num_ += "I"
            num -= 1

print(num_)
```



### *T25353: 排队 （选做）

http://cs101.openjudge.cn/practice/25353/

没做。



## 2. 学习总结和收获



考试过程一波三折，先是第一题看错题，ac了二三四（中间也有一点小错误，键盘不适应导致经常敲错，也启示我要多来机房看看，适应一下这个硬件），然后回去查第一题发现题看错了，前四题做完一个小时不到，后一个小时硬刚第五题失败，主要是因为忘记了使用字典能带来便利，于是写了一大堆重复的if else结构，碰巧我那台电脑鼠标不老实，复制粘贴经常选不中，于是乎时间大幅度延长，并且在考虑头两个字符的时候出了一点差错，查了半天才查出来，最后没时间AC了，至于第六题看了一眼就skip了（）。

 

目前在基础语法方面，应该是掌握得还可以，但是如何调用最合适的语法还需要一些练习来找感觉，另外关于代码的时间复杂度这些内容了解得也并没有很透彻，会结合讲义再继续看下去。每日选做还在追进度的状态，希望早日把进度跟上。。