# 计概每日选做



## 01003:Hangover

- [查看](http://cs101.openjudge.cn/2024fallroutine/01003/)

- 描述

  How far can you make a stack of cards overhang a table? If you have one card, you can create a maximum overhang of half a card length. (We're assuming that the cards must be perpendicular to the table.) With two cards you can make the top card overhang the bottom one by half a card length, and the bottom one overhang the table by a third of a card length, for a total maximum overhang of 1/2 `+` 1/3 `=` 5/6 card lengths. In general you can make *n* cards overhang by 1/2 `+` 1/3 `+` 1/4 `+` ... `+` 1/(*n* `+` 1) card lengths, where the top card overhangs the second by 1/2, the second overhangs tha third by 1/3, the third overhangs the fourth by 1/4, etc., and the bottom card overhangs the table by 1/(*n* `+` 1). This is illustrated in the figure below. 

  ![img](http://media.openjudge.cn/images/1003/hangover.jpg)

- 输入

  The input consists of one or more test cases, followed by a line containing the number 0.00 that signals the end of the input. Each test case is a single line containing a positive floating-point number c whose value is at least 0.01 and at most 5.20; c will contain exactly three digits.

- 输出

  For each test case, output the minimum number of cards necessary to achieve an overhang of at least c card lengths. Use the exact output format shown in the examples.

- 样例输入

  `1.00 3.71 0.04 5.19 0.00 `

- 样例输出

  `3 card(s) 61 card(s) 1 card(s) 273 card(s)`

```
while True:
    length = float(input())
    if length == 0.00:
        break
    else:
        i,length_ = 2,0
        while length_ < length:
            length_ += 1 / i
            i += 1
        print(i-2, "card(s)")
```



## 01008:Maya Calendar

- [查看]([OpenJudge - 01003:Hangover](http://cs101.openjudge.cn/2024fallroutine/01003/))

- 描述

  During his last sabbatical, professor M. A. Ya made a surprising discovery about the old Maya calendar. From an old knotted message, professor discovered that the Maya civilization used a 365 day long year, called Haab, which had 19 months. Each of the first 18 months was 20 days long, and the names of the months were pop, no, zip, zotz, tzec, xul, yoxkin, mol, chen, yax, zac, ceh, mac, kankin, muan, pax, koyab, cumhu. Instead of having names, the days of the months were denoted by numbers starting from 0 to 19. The last month of Haab was called uayet and had 5 days denoted by numbers 0, 1, 2, 3, 4. The Maya believed that this month was unlucky, the court of justice was not in session, the trade stopped, people did not even sweep the floor. For religious purposes, the Maya used another calendar in which the year was called Tzolkin (holly year). The year was divided into thirteen periods, each 20 days long. Each day was denoted by a pair consisting of a number and the name of the day. They used 20 names: imix, ik, akbal, kan, chicchan, cimi, manik, lamat, muluk, ok, chuen, eb, ben, ix, mem, cib, caban, eznab, canac, ahau and 13 numbers; both in cycles. Notice that each day has an unambiguous description. For example, at the beginning of the year the days were described as follows: 1 imix, 2 ik, 3 akbal, 4 kan, 5 chicchan, 6 cimi, 7 manik, 8 lamat, 9 muluk, 10 ok, 11 chuen, 12 eb, 13 ben, 1 ix, 2 mem, 3 cib, 4 caban, 5 eznab, 6 canac, 7 ahau, and again in the next period 8 imix, 9 ik, 10 akbal . . . Years (both Haab and Tzolkin) were denoted by numbers 0, 1, . . . , where the number 0 was the beginning of the world. Thus, the first day was: Haab: 0. pop 0 Tzolkin: 1 imix 0 Help professor M. A. Ya and write a program for him to convert the dates from the Haab calendar to the Tzolkin calendar.

- 输入

  The date in Haab is given in the following format: NumberOfTheDay. Month Year  The first line of the input file contains the number of the input dates in the file. The next n lines contain n dates in the Haab calendar format, each in separate line. The year is smaller then 5000.

- 输出

  The date in Tzolkin should be in the following format: Number NameOfTheDay Year  The first line of the output file contains the number of the output dates. In the next n lines, there are dates in the Tzolkin calendar format, in the order corresponding to the input dates.

- 样例输入

  `3 10. zac 0 0. pop 0 10. zac 1995`

- 样例输出

  `3 3 chuen 0 1 imix 0 9 cimi 2801`

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

  

## 01017:装箱问题

- [查看](http://cs101.openjudge.cn/2024fallroutine/01017/)

- 描述

  一个工厂制造的产品形状都是长方体，它们的高度都是h，长和宽都相等，一共有六个型号，他们的长宽分别为1*1, 2*2, 3*3, 4*4, 5*5, 6*6。这些产品通常使用一个 6*6*h 的长方体包裹包装然后邮寄给客户。因为邮费很贵，所以工厂要想方设法的减小每个订单运送时的包裹数量。他们很需要有一个好的程序帮他们解决这个问题从而节省费用。现在这个程序由你来设计。

- 输入

  输入文件包括几行，每一行代表一个订单。每个订单里的一行包括六个整数，中间用空格隔开，分别为1*1至6*6这六种产品的数量。输入文件将以6个0组成的一行结尾。

- 输出

  除了输入的最后一行6个0以外，输入文件里每一行对应着输出文件的一行，每一行输出一个整数代表对应的订单所需的最小包裹数。

- 样例输入

  `0 0 4 0 0 1  7 5 1 0 0 0  0 0 0 0 0 0 `

- 样例输出

  `2  1 `

- ```
  three_two = [0,5,3,1]
  
  while True:
      lst = list(map(int, input().split()))
      if lst == [0,0,0,0,0,0]:
          break
      else:
          cnt = sum(lst[3:]) + (lst[2] - 1) // 4 + 1 
          if lst[1] > lst[3] * 5 + three_two[lst[2] % 4]: 
              cnt += (lst[1] - lst[3] * 5 - three_two[lst[2] % 4] - 1) // 9 + 1  
          if lst[0] > cnt * 36 - (4 * lst[1] + 9 * lst[2] + 16 * lst[3] + 25 * lst[4] + 36 * lst[5]):
              cnt += (lst[0] - (cnt * 36 - (4 * lst[1] + 9 * lst[2] + 16 * lst[3] + 25 * lst[4] + 36 * lst[5])) - 1) // 36 + 1
          print(cnt)
  ```



## 01218:THE DRUNK JAILER

- [查看](http://cs101.openjudge.cn/2024fallroutine/01218/)

- 描述

  A certain prison contains a long hall of n cells, each right next to each other. Each cell has a prisoner in it, and each cell is locked. One night, the jailer gets bored and decides to play a game. For round 1 of the game, he takes a drink of whiskey,and then runs down the hall unlocking each cell. For round 2, he takes a drink of whiskey, and then runs down the hall locking every other cell (cells 2, 4, 6, ?). For round 3, he takes a drink of whiskey, and then runs down the hall. He visits every third cell (cells 3, 6, 9, ?). If the cell is locked, he unlocks it; if it is unlocked, he locks it. He repeats this for n rounds, takes a final drink, and passes out. Some number of prisoners, possibly zero, realizes that their cells are unlocked and the jailer is incapacitated. They immediately escape. Given the number of cells, determine how many prisoners escape jail.

- 输入

  The first line of input contains a single positive integer. This is the number of lines that follow. Each of the following lines contains a single integer between 5 and 100, inclusive, which is the number of cells n. 

- 输出

  For each line, you must print out the number of prisoners that escape when the prison has n cells. 

- 样例输入

  `2 5 100`

- 样例输出

  `2 10`

  ```
  n = int(input())
  for _ in range(n):
      num = int(input())
      cell = [0] * num
      for i in range(1,num+1):
          for j in range(1,num+1):
              if j % i == 0:
                  cell[j-1] = 1 - cell[j-1]
              else:
                  continue
      print(sum(cell))
  ```



## 01852:Ants

- [查看](http://cs101.openjudge.cn/2024fallroutine/01852/)
- 描述

- An army of ants walk on a horizontal pole of length l cm, each with a constant speed of 1 cm/s. When a walking ant reaches an end of the pole, it immediatelly falls off it. When two ants meet they turn back and start walking in opposite directions. We know the original positions of ants on the pole, unfortunately, we do not know the directions in which the ants are walking. Your task is to compute the earliest and the latest possible times needed for all ants to fall off the pole.

- 输入

  The first line of input contains one integer giving the number of cases that follow. The data for each case start with two integer numbers: the length of the pole (in cm) and n, the number of ants residing on the pole. These two numbers are followed by n integers giving the position of each ant on the pole as the distance measured from the left end of the pole, in no particular order. All input integers are not bigger than 1000000 and they are separated by whitespace.

- 输出

  For each case of input, output two numbers separated by a single space. The first number is the earliest possible time when all ants fall off the pole (if the directions of their walks are chosen appropriately) and the second number is the latest possible such time. 

- 样例输入

  `2 10 3 2 6 7 214 7 11 12 7 13 176 23 191 `

- 样例输出

  `4 8 38 207`

- ```
  cases = int(input())
  for _ in range(cases):
      l,n = map(int,input().split())
      lst = list(map(int,input().split()))
      t_min,t_max = l,0
      for i in range(n):
          if abs(lst[i] - (l / 2)) > t_max:
              t_max = abs(lst[i] - (l / 2))
          if abs(lst[i] - (l / 2)) < t_min:
              t_min = abs(lst[i] - (l / 2))
      t_max = int(t_max + l / 2)
      t_min = int(l / 2 - t_min)
      print(t_min,t_max)
  ```



## 02386:Lake Counting

- [查看](http://cs101.openjudge.cn/2024fallroutine/02386/)
- [提交](http://cs101.openjudge.cn/2024fallroutine/02386/submit/)
- [统计](http://cs101.openjudge.cn/2024fallroutine/02386/statistics/)
- [提问](http://cs101.openjudge.cn/2024fallroutine/clarify/02386/)

- 总时间限制: 

  1000ms

- 内存限制: 

  65536kB

- 描述

  Due to recent rains, water has pooled in various places in Farmer John's field, which is represented by a rectangle of N x M (1 <= N <= 100; 1 <= M <= 100) squares. Each square contains either water ('W') or dry land ('.'). Farmer John would like to figure out how many ponds have formed in his field. A pond is a connected set of squares with water in them, where a square is considered adjacent to all eight of its neighbors.  Given a diagram of Farmer John's field, determine how many ponds he has.

- 输入

  * Line 1: Two space-separated integers: N and M  * Lines 2..N+1: M characters per line representing one row of Farmer John's field. Each character is either 'W' or '.'. The characters do not have spaces between them.

- 输出

  * Line 1: The number of ponds in Farmer John's field.

- 样例输入

  `10 12 W........WW. .WWW.....WWW ....WW...WW. .........WW. .........W.. ..W......W.. .W.W.....WW. W.W.W.....W. .W.W......W. ..W.......W.`

- 样例输出

  `3`

- 提示

  OUTPUT DETAILS:  There are three ponds: one in the upper left, one in the lower left,and one along the right side.

- 

- ```
  import sys
  sys.setrecursionlimit(20000)
  
  def dfs(a,b):
      directions = [[1,1],[1,0],[1,-1],[0,1],[0,-1],[-1,1],[-1,0],[-1,-1]]
      if a < 0 or b < 0 or a >= len(matrix) or b >= len(matrix[0]) or matrix[a][b] == ".":
          return
      matrix[a][b] = "."
      for i in range(len(directions)):
          dfs(a + directions[i][0],b + directions[i][1])
  
  ans = 0
  n,m = map(int,input().split())
  matrix = [["."] * (m + 2) for i in range(n + 2)]
  for _ in range(1,n + 1):
       matrix[_][1:-1] = input()
  for i in range(1,n + 1):
      for j in range(1,m + 1):
          if matrix[i][j] == "W":
              dfs(i,j)
              ans += 1
  print(ans)
  ```



## 02689:大小写字母互换

- [查看](http://cs101.openjudge.cn/2024fallroutine/02689/)

- 描述

  把一个字符串中所有出现的大写字母都替换成小写字母，同时把小写字母替换成大写字母。

- 输入

  输入一行：待互换的字符串。

- 输出

  输出一行：完成互换的字符串（字符串长度小于80）。

- 样例输入

  `If so, you already have a Google Account. You can sign in on the right. `

- 样例输出

  `iF SO, YOU ALREADY HAVE A gOOGLE aCCOUNT. yOU CAN SIGN IN ON THE RIGHT. `

- ```
  a=input()
  b=""
  for i in a:
      if ord(i) >= 65 and ord(i) <= 90:
          b += chr(ord(i) + 32)
      elif ord(i) >= 97 and ord(i) <= 122:
          b += chr(ord(i) - 32)
      else:
          b += i
  print(b)
  ```



## 02692:假币问题

- [查看](http://cs101.openjudge.cn/2024fallroutine/02692/)

- 描述

  赛利有12枚银币。其中有11枚真币和1枚假币。假币看起来和真币没有区别，但是重量不同。但赛利不知道假币比真币轻还是重。于是他向朋友借了一架天平。朋友希望赛利称三次就能找出假币并且确定假币是轻是重。例如:如果赛利用天平称两枚硬币，发现天平平衡，说明两枚都是真的。如果赛利用一枚真币与另一枚银币比较，发现它比真币轻或重，说明它是假币。经过精心安排每次的称量，赛利保证在称三次后确定假币。

- 输入

  第一行有一个数字n，表示有n组测试用例。 对于每组测试用例： 输入有三行，每行表示一次称量的结果。赛利事先将银币标号为A-L。每次称量的结果用三个以空格隔开的字符串表示：天平左边放置的硬币 天平右边放置的硬币 平衡状态。其中平衡状态用``up'', ``down'', 或 ``even''表示, 分别为右端高、右端低和平衡。天平左右的硬币数总是相等的。

- 输出

  输出哪一个标号的银币是假币，并说明它比真币轻还是重(heavy or light)。

- 样例输入

  `1 ABCD EFGH even  ABCI EFJK up  ABIJ EFGH even `

- 样例输出

  `K is the counterfeit coin and it is light. `

- ```
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



## 02701:与7无关的数

- [查看](http://cs101.openjudge.cn/2024fallroutine/02701/)

- 描述

  一个正整数,如果它能被7整除,或者它的十进制表示法中某一位上的数字为7,则称其为与7相关的数.现求所有小于等于n(n < 100)的与7无关的正整数的平方和.

- 输入

  输入为一行,正整数n(n < 100)

- 输出

  输出一行，包含一个整数，即小于等于n的所有与7无关的正整数的平方和。

- 样例输入

  `21`

- 样例输出

  `2336`

- ```
  a = int(input())
  i = 1
  sum = 0
  while i <= a:
      if i % 7 == 0:
          i += 1
      else:
          b = str(i)
          c = 0
          for j in range(len(b)):
              if b[j] == "7":
                  c += 1
              else:
                  c += 0
          if c == 0:
              sum = sum + i ** 2
              i += 1
          else:
              i += 1
  print(sum)
  ```



## 02707:求一元二次方程的根

- [查看](http://cs101.openjudge.cn/2024fallroutine/02707/)

- 描述

  利用公式x1 = (-b + sqrt(b*b-4*a*c))/(2*a), x2 = (-b - sqrt(b*b-4*a*c))/(2*a)求一元二次方程ax2 + bx + c =0的根，其中a不等于0。

- 输入

  第一行是待解方程的数目n。 其余n行每行含三个浮点数a, b, c（它们之间用空格隔开），分别表示方程ax2 + bx + c =0的系数。

- 输出

  输出共有n行，每行是一个方程的根： 若是两个实根，则输出：x1=...;x2 = ... 若两个实根相等，则输出：x1=x2=... 若是两个虚根，则输出：x1=实部+虚部i; x2=实部-虚部i  所有实数部分要求精确到小数点后5位，数字、符号之间没有空格。 x1和x2的顺序：x1的实部>Re的实部||(x1的实部==x2的实部&&x1的虚部>=x2的虚部)

- 样例输入

  `3 1.0 3.0 1.0 2.0 -4.0 2.0 1.0 2.0 8.0 `

- 样例输出

  `x1=-0.38197;x2=-2.61803 x1=x2=1.00000 x1=-1.00000+2.64575i;x2=-1.00000-2.64575i`

- 提示

  1、需要严格按照题目描述的顺序求解x1、x2。 2、方程的根以及其它中间变量用double类型变量表示。 3、函数sqrt()在头文件math.h中。 4、要输出浮点数、双精度数小数点后5位数字，可以用下面这种形式：  printf("%.5f", num);  注意，在使用Java做此题时，可能会出现x1或x2等于-0的情形，此时，需要把负号去掉

- ```
  import math
  
  n = int(input())
  for _ in range(n):
      a,b,c = map(float,input().split())
      if b == 0:
          b = -b
      delta = b ** 2 - 4 * a * c
      p = -b / (2 * a)
      if delta == 0:
          print(f'x1=x2={p:.5f}')
      elif delta > 0:
          x1 = p + math.sqrt(delta) / (2 * a)
          x2 = p - math.sqrt(delta) / (2 * a)
          print(f'x1={x1:.5f};x2={x2:.5f}')
      else:
          delta_ = (math.sqrt(-delta)) / (2 * a)
          print(f'x1={p:.5f}+{delta_:.5f}i;x2={p:.5f}-{delta_:.5f}i')
  ```



## 02733:判断闰年

- [查看](http://cs101.openjudge.cn/2024fallroutine/02733/)

- 描述

  判断某年是否是闰年。

- 输入

  输入只有一行，包含一个整数a(0 < a < 3000)

- 输出

  一行，如果公元a年是闰年输出Y，否则输出N

- 样例输入

  `2006`

- 样例输出

  `N`

- 提示

  公历纪年法中，能被4整除的大多是闰年，但能被100整除而不能被400整除的年份不是闰年， 能被3200整除的也不是闰年，如1900年是平年，2000年是闰年，3200年不是闰年。

- ```
  a = int(input())
  if a % 4 == 0 and a % 100 != 0 or a % 400 == 0:
      print("Y")
  else:
      print("N")
  ```



## 02746:约瑟夫问题

- [查看](http://cs101.openjudge.cn/2024fallroutine/02746/)

- 描述

  约瑟夫问题：有ｎ只猴子，按顺时针方向围成一圈选大王（编号从１到ｎ），从第１号开始报数，一直数到ｍ，数到ｍ的猴子退出圈外，剩下的猴子再接着从1开始报数。就这样，直到圈内只剩下一只猴子时，这个猴子就是猴王，编程求输入ｎ，ｍ后，输出最后猴王的编号。  

- 输入

  每行是用空格分开的两个整数，第一个是 n, 第二个是 m ( 0 < m,n <=300)。最后一行是：  0 0  

- 输出

  对于每行输入数据（最后一行除外)，输出数据也是一行，即最后猴王的编号 

- 样例输入

  `6 2 12 4 8 3 0 0`

- 样例输出

  `5 1 7`

- ```
  while True:
      n,m= map(int,input().split())
      if n == 0 and m == 0:
          break
      else:
          lst = []
          for i in range(1,n+1):
              lst.append(i)
          index = 0
          while len(lst) > 1:
              index = (index + m - 1) % len(lst)
              lst.pop(index)
          print(lst[0])
  ```



## 02750:鸡兔同笼

- [查看](http://cs101.openjudge.cn/2024fallroutine/02750/)

- 描述

  一个笼子里面关了鸡和兔子（鸡有2只脚，兔子有4只脚，没有例外）。已经知道了笼子里面脚的总数a，问笼子里面至少有多少只动物，至多有多少只动物。

- 输入

  一行，一个正整数a (a < 32768)。

- 输出

  一行，包含两个正整数，第一个是最少的动物数，第二个是最多的动物数，两个正整数用一个空格分开。 如果没有满足要求的答案，则输出两个0，中间用一个空格分开。

- 样例输入

  `20 `

- 样例输出

  `5 10`

- ```
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



## 02753:菲波那契数列

- [查看](http://cs101.openjudge.cn/2024fallroutine/02753/)
- 描述

- 菲波那契数列是指这样的数列: 数列的第一个和第二个数都为1，接下来每个数都等于前面2个数之和。 给出一个正整数a，要求菲波那契数列中第a个数是多少。 

- 输入

  第1行是测试数据的组数n，后面跟着n行输入。每组测试数据占1行，包括一个正整数a(1 <= a <= 20)

- 输出

  输出有n行，每行输出对应一个输入。输出应是一个正整数，为菲波那契数列中第a个数的大小

- 样例输入

  `4 5 2 19 1 `

- 样例输出

  `5 1 4181 1`

- ```
  n = int(input())
  for _ in range(n):
      num = int(input())
      a,b = 1,1
      if num == 1 or num == 2:
          print("1")
      else:
          for i in range(1,num):
              a,b = b,a + b
          print(a)
  ```



## 02802:小游戏

- [查看](http://cs101.openjudge.cn/2024fallroutine/02802/)
- [提交](http://cs101.openjudge.cn/2024fallroutine/02802/submit/)
- [统计](http://cs101.openjudge.cn/2024fallroutine/02802/statistics/)
- [提问](http://cs101.openjudge.cn/2024fallroutine/clarify/02802/)

- 总时间限制: 

  1000ms

- 内存限制: 

  65536kB

- 描述

  一天早上，你起床的时候想：“我编程序这么牛，为什么不能靠这个赚点小钱呢？”因此你决定编写一个小游戏。 游戏在一个分割成w * h个正方格子的矩形板上进行。如图所示，每个正方格子上可以有一张游戏卡片，当然也可以没有。 当下面的情况满足时，我们认为两个游戏卡片之间有一条路径相连： 路径只包含水平或者竖直的直线段。路径不能穿过别的游戏卡片。但是允许路径临时的离开矩形板。下面是一个例子：

   ![img](http://media.openjudge.cn/images/1101/1101_1.jpg) 

  这里在 (1, 3)和 (4, 4)处的游戏卡片是可以相连的。而在 (2, 3) 和 (3, 4) 处的游戏卡是不相连的，因为连接他们的每条路径都必须要穿过别的游戏卡片。 你现在要在小游戏里面判断是否存在一条满足题意的路径能连接给定的两个游戏卡片。

- 输入

  输入包括多组数据(不多于10组)。一个矩形板对应一组数据。每组数据包括的第一行包括两个整数w和h (1 <= w, h <= 75)，分别表示矩形板的宽度和长度。下面的h行，每行包括w个字符，表示矩形板上的游戏卡片分布情况。使用‘X’表示这个地方有一个游戏卡片；使用空格表示这个地方没有游戏卡片。  之后的若干行上每行上包括4个整数x1, y1, x2, y2 (1 <= x1, x2 <= w, 1 <= y1, y2 <= h)。给出两个卡片在矩形板上的位置（注意：矩形板左上角的坐标是(1, 1)）。输入保证这两个游戏卡片所处的位置是不相同的。如果一行上有4个0，表示这组测试数据的结束。  如果一行上给出w = h = 0，那么表示所有的输入结束了。

- 输出

  对每一个矩形板，输出一行“Board #n:”，这里n是输入数据的编号。然后对每一组需要测试的游戏卡片输出一行。这一行的开头是“Pair m: ”，这里m是测试卡片的编号（对每个矩形板，编号都从1开始）。接下来，如果可以相连，找到连接这两个卡片的所有路径中包括线段数最少的路径，输出“k segments.”，这里k是找到的最优路径中包括的线段的数目；如果不能相连，输出“impossible.”。  每组数据之后输出一个空行。

- 样例输入

  `5 4 `

  `XXXXX `

  `X   X `

  `XXX X`

  ` XXX  ` 

   `2 3 5 3 `

  `1 3 4 4 `

  `2 3 3 4 `

  `0 0 0 0 `

  `0 0 `

- 样例输出

  `Board #1: Pair 1: 4 segments. `

  `Pair 2: 3 segments. `

  `Pair 3: impossible.`

  ```
  from collections import deque
  
  def bfs(m,n,a,b):
      ans = []
      directions = [[0,1], [1,0], [-1,0], [0,-1]]
      q = deque([(-1,0,(m,n))])
      in_queue = {(-1,(m,n))}
  
      while q:
          d,s,(x,y) = q.popleft()
          if x == a and y == b:
              ans.append(s)
              break
          for i in range(len(directions)):
              nx = x + directions[i][0]
              ny = y + directions[i][1]
              if 0 <= nx < h + 2 and 0 <= ny < w + 2 and ((i, nx, ny) not in in_queue):
                  nd = i
                  if d + nd == 3:
                      continue
                  if nd != d:
                      ns = s + 1
                  else:
                      ns = s
                  if nx == a and ny == b:
                      ans.append(ns)
                  if matrix[nx][ny] != "X":
                      in_queue.add((nd, nx, ny))
                      q.append((nd, ns, (nx, ny)))
  
      if len(ans):
          return str(min(ans)) + " segments."
      else:
          return "impossible."
  
  case_num = 0
  while True:
      w,h = map(int,input().split())
      if w == 0 and h == 0:
          break
      case_num += 1
      print("Board #" + str(case_num) + ":")
      matrix = [[" "] * (w + 2) for i in range(h + 2)]
      for _ in range(1, h + 1):
          matrix[_][1:-1] = map(str, input())
      pair_num = 0
  
      while True:
          y1,x1,y2,x2 = map(int,input().split())
          if y1 == 0 and y2 == 0 and x1 == 0 and x2 == 0:
              break
          pair_num += 1
          situation = bfs(x1,y1,x2,y2)
          print("Pair " + str(pair_num) + ": " + situation)
  
      print()
  ```



## 02808:校门外的树

- [查看](http://cs101.openjudge.cn/2024fallroutine/02808/)

- 描述

  某校大门外长度为L的马路上有一排树，每两棵相邻的树之间的间隔都是1米。我们可以把马路看成一个数轴，马路的一端在数轴0的位置，另一端在L的位置；数轴上的每个整数点，即0，1，2，……，L，都种有一棵树。 马路上有一些区域要用来建地铁，这些区域用它们在数轴上的起始点和终止点表示。已知任一区域的起始点和终止点的坐标都是整数，区域之间可能有重合的部分。现在要把这些区域中的树（包括区域端点处的两棵树）移走。你的任务是计算将这些树都移走后，马路上还有多少棵树。 

- 输入

  输入的第一行有两个整数L（1 <= L <= 10000）和 M（1 <= M <= 100），L代表马路的长度，M代表区域的数目，L和M之间用一个空格隔开。接下来的M行每行包含两个不同的整数，用一个空格隔开，表示一个区域的起始点和终止点的坐标。

- 输出

  输出包括一行，这一行只包含一个整数，表示马路上剩余的树的数目。

- 样例输入

  `500 3 150 300 100 200 470 471 `

- 样例输出

  `298`

- ```
  l,m = map(int,input().split())
  tree = [1] * (l+1)
  
  for _ in range(m):
      a,b = map(int,input().split())
      for i in range(a,b+1):
          tree[i] = 0
  
  print(sum(tree))
  ```



## 02810:完美立方

- [查看](http://cs101.openjudge.cn/2024fallroutine/02810/)
- 描述

- 形如a3= b3 + c3 + d3的等式被称为完美立方等式。例如123= 63 + 83 + 103 。编写一个程序，对任给的正整数N (N≤100)，寻找所有的四元组(a, b, c, d)，使得a3 = b3 + c3 + d3，其中a,b,c,d 大于 1, 小于等于N，且b<=c<=d。

- 输入

  一个正整数N (N≤100)。

- 输出

  每行输出一个完美立方。输出格式为： Cube = a, Triple = (b,c,d) 其中a,b,c,d所在位置分别用实际求出四元组值代入。  请按照a的值，从小到大依次输出。当两个完美立方等式中a的值相同，则b值小的优先输出、仍相同则c值小的优先输出、再相同则d值小的先输出。

- 样例输入

  `24`

- 样例输出

  `Cube = 6, Triple = (3,4,5) Cube = 12, Triple = (6,8,10) Cube = 18, Triple = (2,12,16) Cube = 18, Triple = (9,12,15) Cube = 19, Triple = (3,10,18) Cube = 20, Triple = (7,14,17) Cube = 24, Triple = (12,16,20)`

- ```
  n = int(input())
  for i in range(n+1):
      for j in range(2,i):
          for k in range(j+1,i):
              for l in range(k+1,i):
                  if i ** 3 == j ** 3 + k ** 3 + l ** 3:
                      print("Cube = " + str(i) + ", Triple = (" + str(j) + "," + str(k) + "," + str(l) + ")")
  ```



## 02945:拦截导弹

- [查看](http://cs101.openjudge.cn/2024fallroutine/02945/)

- 描述

  某国为了防御敌国的导弹袭击，开发出一种导弹拦截系统。但是这种导弹拦截系统有一个缺陷：虽然它的第一发炮弹能够到达任意的高度，但是以后每一发炮弹都不能高于前一发的高度。某天，雷达捕捉到敌国的导弹来袭，并观测到导弹依次飞来的高度，请计算这套系统最多能拦截多少导弹。拦截来袭导弹时，必须按来袭导弹袭击的时间顺序，不允许先拦截后面的导弹，再拦截前面的导弹。

- 输入

  输入有两行， 第一行，输入雷达捕捉到的敌国导弹的数量k（k<=25）， 第二行，输入k个正整数，表示k枚导弹的高度，按来袭导弹的袭击时间顺序给出，以空格分隔。 

- 输出

  输出只有一行，包含一个整数，表示最多能拦截多少枚导弹。 

- 样例输入

  `8 300 207 155 300 299 170 158 65 `

- 样例输出

  `6`

- 

- ```
  num = int(input())
  lst = list(map(int, input().split()))
  dp_lst = [1] * num
  
  for i in range(1,num):
      for j in range(i):
          if lst[j] >= lst[i]:
              dp_lst[i] = max(dp_lst[i],dp_lst[j]+1)
  
  print(max(dp_lst))
  ```



## 02981:大整数加法

- [查看](http://cs101.openjudge.cn/2024fallroutine/02981/)

- 描述

  求两个不超过200位的非负整数的和。

- 输入

  有两行，每行是一个不超过200位的非负整数，可能有多余的前导0。

- 输出

  一行，即相加后的结果。结果里不能有多余的前导0，即如果结果是342，那么就不能输出为0342。

- 样例输入

  `22222222222222222222 33333333333333333333`

- 样例输出

  `55555555555555555555`

- 

- ```
  a = int(input())
  b = int(input())
  print(a+b)
  ```



## 03143:验证“歌德巴赫猜想”

- [查看](http://cs101.openjudge.cn/2024fallroutine/03143/)
- 描述

- 验证“歌德巴赫猜想”，即：任意一个大于等于6的偶数均可表示成两个素数之和。

- 输入

  输入只有一个正整数x。(x<=2000)

- 输出

  如果x不是“**大于等于**6的偶数”，则输出一行： Error! 否则输出这个数的**所有**分解形式，形式为： x=y+z 其中x为待验证的数，y和z满足y+z=x，而且y<=z，y和z均是素数。 如果存在多组分解形式，则按照**y的升序**输出所有的分解，每行一个分解表达式。  注意输出**不要**有多余的空格。

- 样例输入

  `输入样例1: 7 输入样例2: 10 输入样例3: 100 `

- 样例输出

  `输出样例1: Error! 输出样例2: 10=3+7 10=5+5 输出样例3: 100=3+97 100=11+89 100=17+83 100=29+71 100=41+59 100=47+53`

- 

- ```
  def ss(num):
      flag = True
      p = 2
      while p <= num // 2:
          if num % p == 0:
              flag = False
              break
          else:
              p += 1
      return flag
  
  a = int(input())
  if a < 6 or a % 2 != 0:
      print("Error!")
  else:
      j = 2
      while j <= a//2:
          if ss(j):
              if ss(a-j):
                  print(str(a)+"="+str(j)+"+"+str(a-j))
                  j += 1
              else:
                  j += 1
          else:
              j += 1
  ```



## 03248:最大公约数

- [查看](http://cs101.openjudge.cn/2024fallroutine/03248/)

- 描述

  给定两个正整数，求它们的最大公约数。

- 输入

  有多组数据，每行为两个正整数，且不超过int可以表示的范围。

- 输出

  行对应输出最大公约数。

- 样例输入

  `4 8 8 6 200 300`

- 样例输出

  `4 2 100`

- 

- ```
  import math
  while True:
      try:
          a,b = map(int,input().split())
          print(math.gcd(a,b))
      except EOFError:
          break
  ```



## 03253:约瑟夫问题No.2

- [查看](http://cs101.openjudge.cn/2024fallroutine/03253/)

- 描述

  n 个小孩围坐成一圈，并按顺时针编号为1,2,…,n，从编号为 p 的小孩顺时针依次报数，由1报到m ，当报到 m 时，该小孩从圈中出去，然后下一个再从1报数，当报到 m 时再出去。如此反复，直至所有的小孩都从圈中出去。请按出去的先后顺序输出小孩的编号。

- 输入

  每行是用空格分开的三个整数，第一个是n,第二个是p,第三个是m (0 < m,n < 300)。最后一行是: 0 0 0

- 输出

  按出圈的顺序输出编号，编号之间以逗号间隔。

- 样例输入

  `8 3 4 0 0 0`

- 样例输出

  `6,2,7,4,3,5,1,8`

- 

- ```
  while True:
      n,p,m = map(int,input().split())
      if n == 0 and p == 0 and m == 0:
          break
      else:
          lst = []
          ans = ""
          for i in range(1,n+1):
              lst.append(i)
          index = p - 1
          while len(lst) > 1:
              index = (index + m - 1) % len(lst)
              ans = ans + str(lst[index]) + ","
              lst.pop(index)
          ans = ans + str(lst[0])
          print(ans
  ```



## 04015:邮箱验证

- [查看](http://cs101.openjudge.cn/2024fallroutine/04015/)

- 描述

  POJ 注册的时候需要用户输入邮箱，验证邮箱的规则包括： 1)有且仅有一个'@'符号 2)'@'和'.'不能出现在字符串的首和尾 3)'@'之后至少要有一个'.'，并且'@'不能和'.'直接相连 满足以上3条的字符串为合法邮箱，否则不合法， 编写程序验证输入是否合法

- 输入

  输入包含若干行，每一行为一个代验证的邮箱地址，长度小于100

- 输出

  每一行输入对应一行输出 如果验证合法，输出 YES 如果验证非法：输出 NO

- 样例输入

  `    .a@b.com    pku@edu.cn    cs101@gmail.com    cs101@gmail`

- 样例输出

  `    NO    YES    YES    NO`



```
while True:
    try:
        flag = True
        email = input()
        if email[0] == "." or email[0] == "@" or email[-1] == "." or email[-1] == "@":
            flag = False
        elif not "@" in email:
            flag = False
        else:
            for i in range(len(email)):
                if email[i] == ".":
                    if email[i+1] == "@":
                        flag = False
                elif email[i] == "@":
                    if email[i+1] == ".":
                        flag = False
                    if not "." in email[i+1:]:
                        flag = False
                    if "@" in email[i+1:]:
                        flag = False
        if flag:
            print("YES")
        else:
            print("NO")

    except EOFError:
        break
```



## 04110:圣诞老人的礼物-Santa Clau’s Gifts

- [查看](http://cs101.openjudge.cn/2024fallroutine/04110/)

- 描述

  圣诞节来临了，在城市A中圣诞老人准备分发糖果，现在有多箱不同的糖果，每箱糖果有自己的价值和重量，每箱糖果都可以拆分成任意散装组合带走。圣诞老人的驯鹿最多只能承受一定重量的糖果，请问圣诞老人最多能带走多大价值的糖果。 

- 输入

  第一行由两个部分组成，分别为糖果箱数正整数n(1 <= n <= 100)，驯鹿能承受的最大重量正整数w（0 < w < 10000），两个数用空格隔开。其余n行每行对应一箱糖果，由两部分组成，分别为一箱糖果的价值正整数v和重量正整数w，中间用空格隔开。

- 输出

  输出圣诞老人能带走的糖果的最大总价值，保留1位小数。输出为一行，以换行符结束。

- 样例输入

  `4 15 100 4 412 8 266 7 591 2`

- 样例输出

  `1193.0`

- 

- ```
  n,w = map(int,input().split())
  lst = [0] * n
  ans = 0
  for _ in range(n):
      lst[_] = list(map(int,input().split()))
  for i in range(n):
      lst[i] = [lst[i][0]/lst[i][1],lst[i][0],lst[i][1]]
  lst.sort(reverse=True)
  for i in range(n):
      if lst[i][2] < w:
          w -= lst[i][2]
          ans += lst[i][1]
      else:
          ans += w * lst[i][0]
          break
  print("{:.1f}".format(ans))
  ```



## 04129:变换的迷宫

- [查看](http://cs101.openjudge.cn/2024fallroutine/04129/)

- 描述

  你现在身处一个R*C 的迷宫中，你的位置用"S" 表示，迷宫的出口用"E" 表示。迷宫中有一些石头，用"#" 表示，还有一些可以随意走动的区域，用"." 表示。初始时间为0 时，你站在地图中标记为"S" 的位置上。你每移动一步（向上下左右方向移动）会花费一个单位时间。你必须一直保持移动，不能停留在原地不走。当前时间是K 的倍数时，迷宫中的石头就会消失，此时你可以走到这些位置上。在其余的时间里，你不能走到石头所在的位置。求你从初始位置走到迷宫出口最少需要花费多少个单位时间。如果无法走到出口，则输出"Oop!"。

- 输入

  第一行是一个正整数 T，表示有 T 组数据。 每组数据的第一行包含三个用空格分开的正整数，分别为 R、C、K。 接下来的 R 行中，每行包含了 C 个字符，分别可能是 "S"、"E"、"#" 或 "."。 其中，0 < T <= 20，0 < R, C <= 100，2 <= K <= 10。

- 输出

  对于每组数据，如果能够走到迷宫的出口，则输出一个正整数，表示最少需要花费的单位时间，否则输出 "Oop!"。

- 样例输入

  `1 6 6 2 ...S.. ...#.. .#.... ...#.. ...#.. ..#E#. `

- 样例输出

  `7`

- 

- ```
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



