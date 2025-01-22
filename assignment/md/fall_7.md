# Assignment #7: Nov Mock Exam立冬



Updated 2201 GMT+8 Oct 29, 2024

2024 fall, Complied by 胡新璞，工学院



## 1.题目



### E07618: 病人排队

sorttings, http://cs101.openjudge.cn/practice/07618/

##### 代码

```
n = int(input())
lst1 = [0] * n
lst = [0] * n
sum = 0
for _ in range(n):
    lst1[_] = list(map(str,input().split()))
for __ in range(n):
    lst1[__][0],lst1[__][1] = int(lst1[__][1]),lst1[__][0]
lst2 = sorted(lst1,reverse = True)
for i in range(n):
    if lst2[i][0] >= 60:
        sum += 1
        if lst2[i][0] == lst2[i-1][0]:
            continue
        else:
            re = 0
            for j in range(n):
                if lst1[j][0] == lst2[i][0]:
                    lst[i+re] = lst1[j][1]
                    re += 1
                    lst2[j][0] == lst2[0][0] + 1
    else:
        break
sum1 = 0
for j in range(n):
    if lst1[j][0] < 60:
        sum1 += 1
        lst[sum+sum1-1]= lst1[j][1]
for k in lst:
    print(k)
```

 

### E23555: 节省存储的矩阵乘法

implementation, matrices, http://cs101.openjudge.cn/practice/23555/

##### 代码

```
n, m1, m2 = map(int, input().split())
matrix_a = [0] * n
matrix_b = [0] * n
matrix = [0] * n
for x in range(n):
    matrix_a[x] = [0] * n
    matrix_b[x] = [0] * n
    matrix[x] = [0] * n
for _ in range(m1):
    a, b, c = map(int, input().split())
    matrix_a[a][b] = c
for __ in range(m2):
    a, b, c = map(int, input().split())
    matrix_b[a][b] = c
for i in range(n):
    for j in range(n):
        for k in range(n):
            matrix[i][j] += matrix_a[i][k] * matrix_b[k][j]
for p in range(n):
    for q in range(n):
        if matrix[p][q] != 0:
            print(p,q,matrix[p][q])
```



###  M18182: 打怪兽

implementation/sortings/data structures,

http://cs101.openjudge.cn/practice/18182/

```
cases = int(input())
for _ in range(cases):
    n,m,b = map(int,input().split())
    dict = {}
    alive = True
    for __ in range(n):
        t,x = map(int,input().split())
        if not t in dict:
            dict[t] = [x]
        else:
            dict[t].append(x)
    for i in dict.keys():
        dict[i].sort(reverse = True)
        dict[i] = sum(dict[i][:m])
    dict_ = sorted(dict.items())
    for j in dict_:
        b -= j[1]
        if b <= 0:
            alive = False
            print(j[0])
            break
    if alive:
        print("alive")
```



### M28780: 零钱兑换3

dp, http://cs101.openjudge.cn/practice/28780/

##### 代码

```
///因为期中考落下了进度比较多，dp基本还是要参照题解才能写出来，所以没有复制这题的代码///
```



### T12757: 阿尔法星人翻译官

implementation, http://cs101.openjudge.cn/practice/12757

##### 代码

```
dict = {"zero":0, "one":1, "two":2, "three":3, "four":4, "five":5, "six":6, "seven":7, "eight":8, "nine":9, "ten":10, "eleven":11, "twelve":12, "thirteen":13, "fourteen":14, "fifteen":15, "sixteen":16, "seventeen":17, "eighteen":18, "nineteen":19, "twenty":20, "thirty":30, "forty":40, "fifty":50, "sixty":60, "seventy":70, "eighty":80, "ninety":90}
def num_change(x):
    num = 0
    current = 0
    for word in x:
        if word in dict:
            current += dict[word]
        elif word == "hundred":
            current *= 100
        elif word == "thousand":
            num += current * 1000
            current = 0
    num += current
    return num
alpha = list(map(str, input().split()))
flag1,flag2 = True,True
if alpha[0] == "negative":
    flag1 = False
    alpha.pop(0)
for i in range(len(alpha)):
    if alpha[i] == "million":
        alpha1 = alpha[:i]
        alpha2 = alpha[i+1:]
        num1,num2 = num_change(alpha1),num_change(alpha2)
        flag2 = False
        break
if flag2:
    num = num_change(alpha)
else:
    num = num1 * 1000000 + num2
if not flag1:
    num = -num
print(num)
```



### T16528: 充实的寒假生活

greedy/dp, cs10117 Final Exam, http://cs101.openjudge.cn/practice/16528/

##### 代码

```
n = int(input())
lst = [0] * n
for _ in range(n):
    lst[_] = list(map(int, input().split()))
    lst[_][0],lst[_][1] = lst[_][1],lst[_][0]
date = sorted(lst)
end = date[0][0]
num = 1
for i in range(1,n):
    if date[i][1] > end:
        num += 1
        end = date[i][0]
print(num)
```





## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

 

牺牲了比较多的时间复习期中考，结果不仅计概也牺牲了期中考也牺牲了，这下是真要牺牲了。一方面是去机房键盘手感和做题手感都不顺，除了矩阵乘法过得比较轻松其他题都几近暴毙，第一题完美踩坑，第三题忘记给字典转成按key排序的写法。复盘发现两道T的题其实没那么难，反而是M的第四题因为我dp还不熟练所以对我来说更有挑战性一些。还发现自己写的代码总是又臭又长，要多看群里和题解学习简化代码的方法。总结：菜就多练，马上要开始恶补了。

 