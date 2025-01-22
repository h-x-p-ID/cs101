# Assignment #B: Dec Mock Exam大雪前一天



Updated 1649 GMT+8 Dec 5, 2024

2024 fall, Complied by 胡新璞，工学院



## 1.题目



### E22548: 机智的股民老张

http://cs101.openjudge.cn/practice/22548/

代码

```
lst = list(map(int,input().split()))
value = [0] * len(lst)
for i in range(len(lst) - 1):
    value[i] = lst[i + 1] - lst[i]
dp = [0] * len(lst)
max_value = 0
for i in range(1,len(lst)):
    dp[i] = max(dp[i-1] + value[i],value[i])
    if dp[i] > max_value:
        max_value = dp[i]
print(max_value)
```

 

### M28701: 炸鸡排

greedy, http://cs101.openjudge.cn/practice/28701/

（主打一个数学方法至上。不过机考的时候应该想不出数学方法罢（悲）。Dp的话就是取前面所有项的和，应该也好写。）

代码

```
n,k = map(int,input().split())
t = list(map(int,input().split()))
t.sort()
s = sum(t)
i = n - 1
while t[i] > s / k:
    s -= t[i]
    i -= 1
    if i < 0:
        break
    k -= 1
print(f"{s / k:.3f}")
```



###  M20744: 土豪购物

dp, http://cs101.openjudge.cn/practice/20744/

代码

```
lst = list(map(int, input().split(",")))
dp1 = [0] * len(lst)
dp2 = [0] * len(lst)
dp1[0],dp2[0] = lst[0],lst[0]
for i in range(1,len(lst)):
    dp1[i] = max(dp1[i - 1] + lst[i],lst[i])
    dp2[i] = max(dp1[i - 1],dp2[i - 1] + lst[i],lst[i])
print(max(max(dp1),max(dp2))
```



### T25561: 2022决战双十一

brute force, dfs, http://cs101.openjudge.cn/practice/25561/

代码

```
ans = float('inf')
def dfs(goods,shops,coupons):
    global ans
    if goods == []:
        discount = [0] * m
        for i in range(m):
            for j in coupons[i]:
                if shops[i] >= j[0]:
                    discount[i] = max(discount[i],j[1])
        ans = min(sum(shops) - sum(discount) - (sum(shops) // 300) * 50,ans)
        return
    for i in range(len(goods[0])):
        shops[goods[0][i][0] - 1] += goods[0][i][1]
        dfs(goods[1:],shops,coupons)
        shops[goods[0][i][0] - 1] -= goods[0][i][1]

n,m = map(int,input().split())
goods = []
coupons = []
shops = [0] * m
ans = float('inf')
for i in range(n):
    goods.append([tuple(map(int,x.split(":"))) for x in list(input().split())])
for j in range(m):
    coupons.append([tuple(map(int,y.split("-"))) for y in list(input().split())])
dfs(goods,shops,coupons)
print(ans)
```



### T20741: 两座孤岛最短距离

dfs, bfs, http://cs101.openjudge.cn/practice/20741/

代码

```
import heapq
def dijkstra(a,b):
    directions = [[0,1],[1,0],[-1,0],[0,-1]]
    q = []
    visited = [[False] * len(matrix[0]) for _ in range(n)]
    heapq.heappush(q,(0,a,b))
    while q:
        step,x,y = heapq.heappop(q)
        if visited[x][y]:
            continue
        visited[x][y] = True
        if matrix[x][y] == 1 and step > 0:
            return step
        for i in range(len(directions)):
            nx = x + directions[i][0]
            ny = y + directions[i][1]
            if 0 <= nx < n and 0 <= ny < len(matrix[0]) and not visited[nx][ny]:
                heapq.heappush(q,(step + 1 - matrix[nx][ny],nx,ny))
n = int(input())
matrix = [list(map(int,input())) for _ in range(n)]
for i in range(n):
    for j in range(len(matrix[0])):
        if matrix[i][j] == 1:
            a,b = i,j
print(dijkstra(a,b))
```



### T28776: 国王游戏

greedy, http://cs101.openjudge.cn/practice/28776

代码

```
n = int(input())
a,b = map(int,input().split())
lst = [list(map(int,input().split())) for i in range(n)]
lst.sort(key = lambda x:(x[0] * x[1]))
ans = 0
for i in range(n):
    if ans < a // lst[i][1]:
        ans = a // lst[i][1]
    a *= lst[i][0]
print(ans)
```





## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

 

第一题写麻烦了，超时两次，土豪购物和炸鸡排没想到对应方法心态爆炸了，于是只过了一个，希望接下来所剩无几的时间里能够补救。贪心的策略还是太难想了，有时候方向靠近但是苦于没有较好的证明思路就不太敢写，对我来说难度很大，群里同学的思路非常值得学习；双十一这种题则是阅读量和代码量让人难受，自己debug的能力也还不足，感觉如果在考场上碰到光是这一题能花掉一个多小时，不知如何是好。