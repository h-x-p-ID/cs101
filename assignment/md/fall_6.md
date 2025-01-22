# Assignment #6: Recursion and DP



Updated 2201 GMT+8 Oct 29, 2024

2024 fall, Complied by 胡新璞，工学院



## 1.题目



### sy119: 汉诺塔

recursion, https://sunnywhy.com/sfbj/4/3/119 

代码

```
def moves(a,b,c,num):
    if num == 1:
        print(a+"->"+c)
        return 1
    else:
        m = moves(a,c,b,num-1)
        print(a+"->"+c)
        m += 1
        m += moves(b,a,c,num-1)
        return m

n = int(input())
print(2 ** n - 1)
moves("A","B","C",n)
```

 

### sy132: 全排列I

recursion, https://sunnywhy.com/sfbj/4/3/132

代码

```
def perm(num1,num,num_used,lst,lst_perm):
    if num1 > num:
        lst_perm.append(lst.copy())
        return
    for i in range(1,n+1):
        if num_used[i] == 0:
            lst.append(i)
            num_used[i] = 1
            perm(num1+1,num,num_used,lst,lst_perm)
            num_used[i] = 0
            lst.pop()

n = int(input())
lst_perm = []
perm(1,n,[0] * (n+1),[],lst_perm)
for i in lst_perm:
    print(" ".join(map(str,i)))
```



### 02945: 拦截导弹 

dp, http://cs101.openjudge.cn/2024fallroutine/02945

代码

```
num = int(input())
lst = list(map(int, input().split()))
dp_lst = [1] * num

for i in range(1,num):
    for j in range(i):
        if lst[j] >= lst[i]:
            dp_lst[i] = max(dp_lst[i],dp_lst[j]+1)

print(max(dp_lst))
```



### 23421: 小偷背包 

dp, http://cs101.openjudge.cn/practice/23421

代码

```
n,b = map(int,input().split())
cost = list(map(int,input().split()))
weight = list(map(int,input().split()))

dp = [[0] * (b+1) for _ in range(n+1)]
for i in range(1,n+1):
    for j in range(b+1):
        if weight[i-1] <= j:
            dp[i][j] = max(dp[i-1][j], dp[i-1][j-weight[i-1]] + cost[i-1])
        else:
            dp[i][j] = dp[i-1][j]

print(max(max(dp)))
```



### 02754: 八皇后

dfs and similar, http://cs101.openjudge.cn/practice/02754

代码

```

```



### 189A. Cut Ribbon 

brute force, dp 1300 https://codeforces.com/problemset/problem/189/A

代码

```

```





## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

 

期中周和计算概论疑似同时向我开炮，感觉抽不出时间学，勉强过了一遍知识一开始写代码就是依托，思路勉强能够整理出来，到了写程序的时候就开始东多一点西丢一点，最后还是大部分要参照题解才能AC，不然就是WA大刷屏，跟之前的感觉反了过来，希望期中之后能够集中精力把难点突破掉。

 