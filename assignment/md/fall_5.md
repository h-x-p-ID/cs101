# Assignment #5: Greedy穷举Implementation



Updated 1939 GMT+8 Oct 21, 2024

2024 fall, Complied by 胡新璞，工学院



## 1.题目



### 04148: 生理周期

brute force, http://cs101.openjudge.cn/practice/04148

代码

```
case = 0
while True:
    p,e,i,d = map(int,input().split())
    if p == -1 and e == -1 and i == -1 and d == -1:
        break
    else:
        case += 1
        for k in range(d+1,d+21253):
            if k % 23 == p % 23 and k % 28 == e % 28 and k % 33 == i % 33:
                print("Case " + str(case) + ": the next triple peak occurs in " + str(k - d) + " days.")
                break
```

 

### 18211: 军备竞赛

greedy, two pointers, http://cs101.openjudge.cn/practice/18211

代码

```
p = int(input())
lst = list(map(int, input().split()))
num = 0
weapon = sorted(lst)
buy, sell = 0, len(lst)-1
while buy <= sell:
    if num < 0:
        num = 0
        break
    else:
        if p >= weapon[buy]:
            num += 1
            p -= weapon[buy]
            buy += 1
        else:
            if buy == sell:
                break
            else:
                num -= 1
                p += weapon[sell]
                sell -= 1
print(num)
```



### 21554: 排队做实验

greedy, http://cs101.openjudge.cn/practice/21554

代码

```
a = int(input())
num = int(input())
lst = list(map(int, input().split()))
lst1 = sorted([item for item in lst])
stu = [0] * num
ans = 0
for i in range(num):
    m = min(lst1)
    ans += (num - i - 1) * m
    stu[i] = lst.index(m) + 1
    lst[lst.index(m)] = max(lst) + 1
    lst1.pop(lst1.index(m))
print(" ".join(map(str, stu)))
print(f"{ans / num:.2f}")
```



### 01008: Maya Calendar

implementation, http://cs101.openjudge.cn/practice/01008/

代码

```
dic_h = {"pop":1,"no":2,"zip":3,"zotz":4,"tzec":5,"xul":6,"yoxkin":7,"mol":8,"chen":9,"yax":10,"zac":11,"ceh":12,"mac":13,"kankin":14,"muan":15,"pax":16,"koyab":17,"cumhu":18,"uayet":19}
dic_t = {1:"imix",2:"ik",3:"akbal",4:"kan",5:"chicchan",6:"cimi",7:"manik",8:"lamat",9:"muluk",10:"ok",11:"chuen",12:"eb",13:"ben",14:"ix",15:"mem",16:"cib",17:"caban",18:"eznab",19:"canac",20:"ahau"}
n = int(input())
print(n)
for _ in range(n):
    day_h,month_h,year_h = map(str,input().split())
    day_h,month_h,year_h = int(day_h[:-1]),dic_h[month_h],int(year_h)
    date = year_h * 365 + (month_h - 1) * 20 + day_h + 1
    year_t = (date - 1) // 260
    day_t_str = dic_t[(date - 1) % 260 % 20 + 1]
    day_t_int = (date - 1) % 260 % 13 + 1
    print(day_t_int,day_t_str,year_t)

```



### 545C. Woodcutters

dp, greedy, 1500, https://codeforces.com/problemset/problem/545/C

代码

```
n = int(input())
c = [0] * n
t = [0] * n
if n == 1:
    print("1")
else:
    ans = 2
    for _ in range(n):
        ci,ti = map(int, input().split())
        c[_],t[_] = ci,ti
    for i in range(1,n-1):
        if t[i] < c[i] - c[i-1]:
            ans += 1
        elif t[i] < c[i+1] -c[i]:
            ans += 1
            c[i] += t[i]
        else:
            continue
print(ans)
```



### 01328: Radar Installation

greedy, http://cs101.openjudge.cn/practice/01328/

代码

```
没做。
```





## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

 

作业前五题其实25号就已经写完了，本来想做第六题，但是难度有点大，以及复习期中考试没什么时间，就耽搁了。前五题难度也比之前要大，第一题先用穷举爆算了一遍，然后学了一下中国剩余定理的解法；第二题想了好一会，再去学习了一下双指针的知识才勉强能解决。这周的题目对我来说还有个特色就是都要先WA几遍，有时候没有样例数据还会傻掉找不出bug（比如年份转换，考虑一年的最后一天那种情况）。每日选做最近也没怎么做，期中考之后努力补上。