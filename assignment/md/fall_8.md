# Assignment #8: 田忌赛马来了



Updated 1021 GMT+8 Nov 12, 2024

2024 fall, Complied by 胡新璞，工学院



## 1.题目



### 12558: 岛屿周⻓

matices, http://cs101.openjudge.cn/practice/12558/ 

代码

```
dict = {1:3,2:2,3:1,4:0}
n,m = map(int,input().split())
matrix = [list(map(int, input().split())) for _ in range(n)]
matrix_ = [[0] * (m + 2) for _ in range(n + 2)]
c = 0
for i in range(n):
    for j in range(m):
        matrix_[i+1][j+1] = matrix[i][j]
for i in range(n):
    for j in range(m):
        if matrix_[i+1][j+1] == 1:
            lst = [matrix_[i][j+1],matrix_[i+1][j],matrix_[i+1][j+2],matrix_[i+2][j+1]]
            c += dict[sum(lst)]
print(c)
```

 

### LeetCode54.螺旋矩阵

matrice, https://leetcode.cn/problems/spiral-matrix/

与OJ这个题目一样的 18106: 螺旋矩阵，

http://cs101.openjudge.cn/practice/18106

代码

```
n = int(input())
matrix = [[0] * n for _ in range(n)]
directions = [[1,0],[0,1],[-1,0],[0,-1]]
d = 0
col,row = 0,0
for i in range(1,n ** 2 + 1):
    matrix[col][row] = i
    if row + directions[d][0] == n or col + directions[d][1] == n or matrix[col + directions[d][1]][row + directions[d][0]] != 0:
        d = (d + 1) % 4
    row = row + directions[d][0]
    col = col + directions[d][1]
for i in range(n):
    print(" ".join(map(str, matrix[i])))
```



###  04133:垃圾炸弹

matrices, http://cs101.openjudge.cn/practice/04133/

代码

```
d = int(input())
n = int(input())
matrix = [[0] * 1025 for _ in range(1025)]
for _ in range(n):
    x,y,ii = map(int,input().split())
    for i in range(max(0, x - d), min(1025, x + d + 1)):
        for j in range(max(0, y - d), min(1025, y + d + 1)):
            matrix[i][j] += ii
cnt = 0
max_trash = 0
for i in range(1025):
    for j in range(1025):
        if matrix[i][j] > max_trash:
            max_trash = matrix[i][j]
            cnt = 1
        elif matrix[i][j] == max_trash:
            cnt += 1
print(cnt,max_trash)
```



### LeetCode376.摆动序列

greedy, dp, https://leetcode.cn/problems/wiggle-subsequence/

与OJ这个题目一样的，26976:摆动序列, http://cs101.openjudge.cn/routine/26976/

思路跟oj题解上胡睿诚学长的思路相仿，但是在后续处理的时候被卡住了，没有想到用sgn（x）（也就是这里k = lst[i] // **abs**(lst[i])这一步）来处理，导致本来写得有点啰嗦，受启发得以简化。关于出现连续不变的项的写法也参照了题解，自己写的绕来绕去绕晕了。

代码

```
n = int(input())
num = list(map(int,input().split()))
lst = [0] * (n - 1)
for i in range(n-1):
    lst[i] = num[i+1] - num[i]
k = 0
len_num = 1
for i in range(n-1):
    if lst[i] * k < 0 or (k == 0 and lst[i] != 0):
        len_num += 1
        k = lst[i] // abs(lst[i])
print(len_num)
```



### CF455A: Boredom

dp, 1500, https://codeforces.com/contest/455/problem/A

代码

```

```



### 02287: Tian Ji -- The Horse Racing

greedy, dfs http://cs101.openjudge.cn/practice/02287

代码

```

```





## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

 

前三道题难度还是比较小的，思路也基本清晰，第四题开始难度就上来了，特别是后两题折磨了我小半个下午还是没解决，终究还是进度没赶上，水平还没提上来。每日选做正在填坑，思路最近有打开一点，有种死人微活的感觉。

 