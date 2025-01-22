# assignment 1

#### 02733: 判断闰年

```
a = int(input())
if a % 4 == 0 and a % 100 != 0 or a % 400 == 0:
    print("Y")
else:
    print("N")
```

![image-20250122225254552](C:\Users\35343\AppData\Roaming\Typora\typora-user-images\image-20250122225254552.png)



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

![](C:\Users\35343\AppData\Roaming\Typora\typora-user-images\image-20250122225323710.png)



#### 50A. Domino piling 2min

```
a,b = map(int,input().split())
print(a * b // 2)
```

![](C:\Users\35343\AppData\Roaming\Typora\typora-user-images\image-20250122225433465.png)



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

![](C:\Users\35343\AppData\Roaming\Typora\typora-user-images\image-20250122225455140.png)



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

![](C:\Users\35343\AppData\Roaming\Typora\typora-user-images\image-20250122225521214.png)



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

![](C:\Users\35343\AppData\Roaming\Typora\typora-user-images\image-20250122225547628.png)



