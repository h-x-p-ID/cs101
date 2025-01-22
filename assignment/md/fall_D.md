# Assignment #D: 十全十美 



Updated 1254 GMT+8 Dec 17, 2024

2024 fall, Complied by 胡新璞，工学院



## 1.题目



### 02692: 假币问题

brute force, http://cs101.openjudge.cn/practice/02692

思路：先遍历十二枚硬币找到假币即可，只需要重新代入表达式就能快速判断轻重。对于假币，它不能出现在结果为even的称量中，且要么同时出现在结果为up的天平右侧和结果为down的天平左侧（即light），要么反之（即heavy）。

代码

```
def is_counterfeit(coin,s):
    condition = []
    for i in range(3):
        if s[i][-1] == "even":
            if coin in s[i][0] + s[i][1]:
                return True
        elif s[i][-1] == "up":
            if not coin in s[i][0] + s[i][1]:
                return True
            else:
                condition.append("heavy") if coin in s[i][0] else condition.append("light")
        elif s[i][-1] == "down":
            if not coin in s[i][0] + s[i][1]:
                return True
            else:
                condition.append("light") if coin in s[i][0] else condition.append("heavy")
    if len(condition) >= 2:
        for i in range(len(condition) - 1):
            if condition[i] != condition[i + 1]:
                return True
    return False
cases = int(input())
for _ in range(cases):
    lst = ["A","B","C","D","E","F","G","H","I","J","K","L"]
    s1 = input().split()
    s2 = input().split()
    s3 = input().split()
    s1[0],s2[0],s3[0] = list(s1[0]),list(s2[0]),list(s3[0])
    s1[1],s2[1],s3[1] = list(s1[1]),list(s2[1]),list(s3[1])
    s_lst = [s1, s2, s3]
    for i in range(len(lst)):
        flag = is_counterfeit(lst[i],s_lst)
        if not flag:
            for j in range(3):
                if s_lst[j][-1] != "even":
                    if lst[i] in s_lst[j][0]:
                        situation = "heavy" if s_lst[j][-1] == "up" else "light"
                    else:
                        situation = "light" if s_lst[j][-1] == "up" else "heavy"
            print(lst[i] + " is the counterfeit coin and it is " + situation + ".")
```

 

### 01088: 滑雪

dp, dfs similar, http://cs101.openjudge.cn/practice/01088

代码

```
def dfs(x, y):
    directions = [[1, 0], [0, 1], [-1, 0], [0, -1]]
    if dp[x][y] > 1:
        return dp[x][y]
    for i in range(len(directions)):
        nx = x + directions[i][0]
        ny = y + directions[i][1]
        if matrix[nx][ny] < matrix[x][y]:
            dp[x][y] = max(dp[x][y], dfs(nx, ny) + 1)
    return dp[x][y]

r,c = map(int,input().split())
matrix = [[10001] * (c + 2) for _ in range(r + 2)]
for i in range(1,r + 1):
    matrix[i][1:c + 1] = list(map(int, input().split()))
dp = [[1] * (c + 2) for _ in range(r + 2)]
ans = 0
for i in range(1,r + 1):
    for j in range(1,c + 1):
        ans = max(ans,dfs(i,j))
print(ans)
```



###  25572: 螃蟹采蘑菇

bfs, dfs, http://cs101.openjudge.cn/practice/25572/

代码

```
from collections import deque
def bfs(a1,b1,a2,b2,u,v):
    directions = [[1,0],[0,1],[-1,0],[0,-1]]
    q1, q2 = deque([(a1,b1)]),deque([(a2,b2)])
    in_queue1, in_queue2 = {(a1,b1)},{(a2,b2)}
    while q1:
        x1, y1 = q1.popleft()
        x2, y2 = q2.popleft()
        if (x1 == u and y1 == v) or (x2 == u and y2 == v):
            return "yes"
        for i in range(len(directions)):
            nx1, ny1 = x1 + directions[i][0], y1 + directions[i][1]
            nx2, ny2 = x2 + directions[i][0], y2 + directions[i][1]
            if 0 <= nx1 < n + 2 and 0 <= ny1 < n + 2 and 0 <= nx2 < n + 2 and 0 <= ny2 < n + 2 and ((nx1,ny1) not in in_queue1 and (nx2,ny2) not in in_queue2):
                if matrix[nx1][ny1] != 1 and matrix[nx2][ny2] != 1:
                    q1.append((nx1,ny1))
                    q2.append((nx2,ny2))
                    in_queue1.add((nx1,ny1))
                    in_queue2.add((nx2,ny2))
    return "no"
n = int(input())
matrix = [[1] * (n + 2) for _ in range(n + 2)]
for _ in range(1,n + 1):
    matrix[_][1:n + 1] = list(map(int, input().split()))
cnt = 0
for i in range(1,n + 1):
    for j in range(1,n + 1):
        if matrix[i][j] == 5 and cnt == 0:
            x1,y1 = i,j
            cnt += 1
        if matrix[i][j] == 5 and cnt == 1:
            x2,y2 = i,j
        if matrix[i][j] == 9:
            x3,y3 = i,j
print(bfs(x1,y1,x2,y2,x3,y3))
```



### 27373: 最大整数

dp, http://cs101.openjudge.cn/practice/27373/

dp部分还是不会，参考了老师发的ai题解。

代码

```
m = int(input())
n = int(input())
lst = list(map(str,input().split()))
lst.sort(key = lambda x: x * 10, reverse = True)
dp = [0] * (m + 1)
for num in lst:
    for i in range(m, len(num) - 1,-1):
        dp[i] = max(dp[i], dp[i - len(num)] * (10 ** len(num)) + int(num))
print(dp[m])
```



### 02811: 熄灯问题

brute force, http://cs101.openjudge.cn/practice/02811

假币问题会，这个题就不会了，对于穷举问题的思路还是遇到难的就发癫，会不了一点。对着题解写了一遍，努力理解了题解的每一步在干什么。

代码

```
n = 5
m = 6
matrix = [[0] * (m + 2) for _ in range(n + 2)]
for i in range(1,n + 1):
    matrix[i][1:m + 1] = list(map(int,input().split()))
ans = [[0] * m for i in range(n)]
def click(i,j):
    ans[i][j] = 1 - ans[i][j]
    for x, y in [(i - 1, j), (i, j - 1), (i, j), (i, j + 1), (i + 1, j)]:
        matrix[x + 1][y + 1] = 1 - matrix[x + 1][y + 1]
def play():
    for j in range(1,m):
        for i in range(n):
            if matrix[i + 1][j] == 1:
                click(i,j)
play()
for i in range(n):
    if matrix[i + 1][m] == 1:
        click(i,0)
play()
for i in range(n):
    print(" ".join(str(x) for x in ans[i]))
```



### 08210: 河中跳房子

binary search, greedy, http://cs101.openjudge.cn/practice/08210/

同上，参照题解写了

代码

```
def check(x):
    num = 0
    now = 0
    for i in range(1, n + 2):
        if rock[i] - now < x:
            num += 1
        else:
            now = rock[i]
    if num > m:
        return True
    else:
        return False
L, n, m = map(int, input().split())
rock = [0]
for i in range(n):
    rock.append(int(input()))
rock.append(L)
lo, hi = 0, L + 1
ans = -1
while lo < hi:
    mid = (lo + hi) // 2

    if check(mid):
        hi = mid
    else:
        ans = mid 
        lo = mid + 1
print(ans)
```





## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

 

最后一周的作业体感真的好难……前三个题还算可以独立做出，但是三个题做下来就花了远不止两小时吧……后三个题基本是潜水在群里学了好几天同学们的代码，才敢结合题解和注释动手试着写写。还剩两天，希望能做好cheatsheet，把基本题目再练练，争取机考有个基础的成绩吧，加油。