# Assignment #C: 五味杂陈



Updated 1148 GMT+8 Dec 10, 2024

2024 fall, Complied by 胡新璞，工学院



## 1.题目



### 1115. 取石子游戏

dfs, https://www.acwing.com/problem/content/description/1117/

代码

```
while True:
    a,b = map(int,input().split())
    if a == b == 0:
        break
    else:
        cnt = 0
        while int(max(a,b) / min(a,b)) < 2:
            if a == b:
                break
            elif a > b:
                cnt += 1
                a -= b
            elif a < b:
                cnt += 1
                b -= a
        print("win" if cnt % 2 == 0 else "lose")
```

 

### 25570: 洋葱

Matrices, http://cs101.openjudge.cn/practice/25570

代码

```
n = int(input())
matrix = [list(map(int, input().split())) for i in range(n)]
ans = 0
directions = [[1,0],[0,1],[-1,0],[0,-1]]
d = 0
for i in range(n // 2):
    col,row = i,i
    cnt = 0
    step = 0
    while not(col == i and row == i and step > 0):
        cnt += matrix[col][row]
        if row + directions[d][0] == n - i or col + directions[d][1] == n - i or row + directions[d][0] == i - 1 or col + directions[d][1] == i - 1:
            d = (d + 1) % 4
        row = row + directions[d][0]
        col = col + directions[d][1]
        step += 1
    ans = max(ans, cnt)
if n % 2 == 1:
    ans = max(ans, matrix[n // 2][n // 2])
print(ans)
```



###  1526C1. Potions(Easy Version)

greedy, dp, data structures, brute force, *1500,

 https://codeforces.com/problemset/problem/1526/C1

代码

```
n = int(input())
potions = list(map(int, input().split()))
potions_negative = []
health = 0
cnt = 0
for i in range(n):
    if potions[i] >= 0:
        health += potions[i]
        cnt += 1
    else:
        potions_negative.append(potions[i])
        health += potions[i]
        cnt += 1
        while health < 0:
            health -= min(potions_negative)
            potions_negative.remove(min(potions_negative))
            cnt -= 1
print(cnt)
```



### 22067: 快速堆猪

辅助栈，http://cs101.openjudge.cn/practice/22067/

代码

```
pigs = []
min_pig = []
while True:
    try:
        s = str(input())
        if s[0:2] == "pu":
            pig = int(s[5:])
            pigs.append(pig)
            if min_pig:
                min_pig.append(min(pig,min_pig[-1]))
            else:
                min_pig.append(pig)
        if s[0:2] == "po":
            if pigs:
                pigs.pop()
                if min_pig:
                    min_pig.pop()
        if s[0:2] == "mi":
            if min_pig:
                print(min_pig[-1])
    except EOFError:
        break
```



### 20106: 走山路

Dijkstra, http://cs101.openjudge.cn/practice/20106/

代码

```
import heapq 
def dijkstra(a,b,u,v):
    directions = [[0, 1], [1, 0], [-1, 0], [0, -1]]
    q = []
    dic = {(a,b):0}
    heapq.heappush(q, (0, a, b))
    while q:
        step, x, y = heapq.heappop(q)
        if x == u and y == v:
            return step
        for i in range(len(directions)):
            nx = x + directions[i][0]
            ny = y + directions[i][1]
            if 0 <= nx < m and 0 <= ny < n and matrix[nx][ny] != "#":
                new_step = step + abs(int(matrix[nx][ny]) - int(matrix[x][y]))
                if (nx,ny) not in dic or new_step < dic[(nx,ny)]:
                    dic[(nx,ny)] = new_step
                    heapq.heappush(q, (new_step, nx, ny))
    return "NO"
m,n,p = map(int,input().split())
matrix = [list(map(str,input().split())) for i in range(m)]
for _ in range(p):
    x1,y1,x2,y2 = map(int,input().split())
    if matrix[x1][y1] == "#" or matrix[x2][y2] == "#":
        print("NO")
    else:
        print(dijkstra(x1,y1,x2,y2))
```



### 04129: 变换的迷宫

bfs, http://cs101.openjudge.cn/practice/04129/

代码

```
from collections import deque
def bfs(a,b,m,n):
    directions = [[1,0],[0,1],[-1,0],[0,-1]]
    q = deque([(0,a,b)])
    in_queue = {(0,a,b)}
    while q:
        time,x,y = q.popleft()
        if x == m and y == n:
            return time
        for i in range(len(directions)):
            nx = x + directions[i][0]
            ny = y + directions[i][1]
            t = (time + 1) % k
            if 0 <= nx < r and 0 <= ny < c and (t,nx,ny) not in in_queue:
                if t == 0 or matrix[nx][ny] != "#":
                    q.append((time + 1,nx,ny))
                    in_queue.add((t,nx,ny))
    return "Oop!"
t = int(input())
for _ in range(t):
    r,c,k = map(int,input().split())
    matrix = [list(map(str,input())) for _ in range(r)]
    for i in range(r):
        for j in range(c):
            if matrix[i][j] == 'S':
                x1,y1 = i,j
            if matrix[i][j] == 'E':
                x2,y2 = i,j
    print(bfs(x1,y1,x2,y2))
```





## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

 

这周题目综合性强，让我有机会再次复习讲过的重要知识点。在时间足够的情况下能自己独立做出前4个题，后两题还需要参考题解，感觉跟模板略有不同就会有点手忙脚乱，有时候明白大致思路但是写不出能够解决问题的代码。以及debug真的很麻烦，这两题一开始死活过不去都是因为某些地方判断语句写错比如最后一题的r,c下意识写了m,n半天才查出来……感觉期末机考如果持平这个难度压力会很大。