# Assignment #4: T-primes + 贪心



Updated 0337 GMT+8 Oct 15, 2024

2024 fall, Complied by 胡新璞，工学院



## 1.题目



### 34B. Sale

greedy, sorting, 900, https://codeforces.com/problemset/problem/34/B

##### 代码

```
a,b = map(int,input().split())
tv = list(map(int,input().split()))
buy_tv = []
for i in range(a):
    if tv[i] <= 0:
        buy_tv.append(tv[i])
num = len(buy_tv)
while num > b:
    index = buy_tv.index(max(buy_tv))
    buy_tv.pop(index)
    num -= 1
print(-sum(buy_tv))
```

 

### 160A. Twins

greedy, sortings, 900, https://codeforces.com/problemset/problem/160/A

##### 代码

```
num = int(input())
lst = list(map(int, input().split()))
coins,coins_num,coins_sum = 0,0,sum(lst) / 2
while coins <= coins_sum:
    coins += max(lst)
    coins_num += 1
    lst.pop(lst.index(max(lst)))
print(coins_num)
```



### 1879B. Chips on the Board

constructive algorithms, greedy, 900, 

https://codeforces.com/problemset/problem/1879/B

##### 代码

```
a = int(input())
for _ in range(a):
    num = int(input())
    lst_row = list(map(int, input().split()))
    lst_col = list(map(int, input().split()))
    print(min(min(lst_row) * num + sum(lst_col), min(lst_col) * num + sum(lst_row)))
```





### 158B. Taxi

*special problem, greedy, implementation, 1100, 

https://codeforces.com/problemset/problem/158/B

##### 代码

```
num = int(input())
taxis = 0
lst = list(map(int, input().split()))
lst1 = [0,0,0,0]
for i in range(num):
    lst1[lst[i]-1] += 1
taxis += lst1[3] + min(lst1[2],lst1[0]) + lst1[1] // 2 + (lst1[2] - min(lst1[2],lst1[0])) + (lst1[0] - min(lst1[2],lst1[0])) // 4
if (lst1[0]-min(lst1[2],lst1[0])) % 4 + lst1[1] % 2 > 4 or lst1[1] % 2 == 1 and (lst1[0]-min(lst1[2],lst1[0])) % 4 == 3:
    taxis += 2
elif (lst1[0]-min(lst1[2],lst1[0])) % 4 + lst1[1] % 2 == 0:
    taxis += 0
else:
    taxis += 1
print(taxis)
```



### *230B. T-primes（选做）

binary search, implementation, math, number theory, 1300, 

http://codeforces.com/problemset/problem/230/B

##### 代码

```
我再研究研究不超时的做法。。。
```



### *12559: 最大最小整数 （选做）

greedy, strings, sortings, http://cs101.openjudge.cn/practice/12559

##### 代码

```
num = int(input())
lst = list(map(str,input().split()))
lst_copy = [item for item in lst]
max_len = len(max(lst,key=len))
for i in range(len(lst)):
    while len(lst[i]) <= max_len:
        lst[i] = lst[i] + lst[i]
zipped_lst = list(zip(lst,lst_copy))
zipped_lst_sorted1 = sorted(zipped_lst)
zipped_lst_sorted2 = sorted(zipped_lst, reverse=True)
sorted_lst1, sorted_lst_copy1 = zip(*zipped_lst_sorted1)
sorted_lst2, sorted_lst_copy2 = zip(*zipped_lst_sorted2)
sorted_lst_copy1 = list(sorted_lst_copy1)
sorted_lst_copy2 = list(sorted_lst_copy2)
min_num = "".join(sorted_lst_copy1)
max_num = "".join(sorted_lst_copy2)
print(max_num,min_num)
```





## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

 

上周其他科目花的时间多，基本没什么时间敲代码……今天做题的时候感觉明显手生，以及题目难度大，还是应该每天抽时间学习。感觉贪心部分策略很重要，有了好的策略或者对题目的理解之后，代码真的只是相对来说蛮简单的一个过程。但是这个前面的策略还是对我来说挺难的，要多做题看讲义来熟悉。