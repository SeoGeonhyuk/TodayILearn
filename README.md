# TodayILearn
2023-1학기 여름방학 모각소를 위한 TIL 레포지토리<br>
https://github.com/SeoGeonhyuk/Backjoon.git<br>
기본적으로 모든 문제 풀이 코드는 위 링크의 깃허브에 커밋하고 있습니다.<br>
# 구현한 알고리즘 정리
## 이진탐색
```
def binarySearch(s, i, min, max):
  if min > max:
    return 0
  mid = (min + max) // 2
  if s[mid] == i:
    return 1
  elif s[mid] > i:
    return binarySearch(s, i, min, mid - 1)
  elif s[mid] < i:
    return binarySearch(s, i, mid + 1, max)
```
## 에라스토테네스의 체
```
n = 10000 #n이하까지 구할 소수
a = [False,False] + [True]*(n-1)
decimal = []
for i in range(2,n+1):
  if a[i]:
    decimal.append(i)
    for j in range(2*i, n+1, i):
        a[j] = False
```
## BFS
```
BFS = []
BFSList = [s[2]]
BFSListVisited = [False] * (s[0] + 1)
BFSListVisited[s[2]] = True

while len(BFSList) != 0:
    start = BFSList.pop(0)
    BFS.append(start)
    for i in vertex[start]:
        if not BFSListVisited[i]:
            BFSListVisited[i] = True
            BFSList.append(i)
```
## DFS
```
def DFST(DFS, DFSList, DFSListVisited, vertex):
  start = DFSList.pop(0)
  if not DFSListVisited[start]:
    DFS.append(start)
    DFSListVisited[start] = True
  for i in vertex[start]:
    if not DFSListVisited[i]:
      DFSList.append(i)
      DFST(DFS, DFSList, DFSListVisited, vertex)
```
# 2023.07.05
백준 6064번 문제<br>
https://www.acmicpc.net/problem/6064<br>
중국인의 나머지 정리 공부<br>
유클리드 호제법을 이용할 경우 최대공약수를 쉽게 구할 수 있다.<br>
파이썬을 이용하여 코드를 작성할 경우 다음과 같다.<br>
```
def gcd(a, b):
    if b == 0:
        return a
    else:
        return gcd(b, a % b)
```
이 호제법에서는 특정한 법칙이 적용되는데 이에 대한 법칙 3가지는 다음과 같다.<br>
1. gcd(a, b) = gcd(b, a)<br>
2. gcd(a, 0) = a<br>
3. gcd(a, b) = gcd(a (mod b), b)<br>
# 2023.07.07
https://www.acmicpc.net/problem/1260<br>
백준 1260번 DFS와 BFS를 풀면서 느낀점<br>
1.최적화하는 방법은 무궁무진하게 많다.<br>
2.예전에만 쓰고 지금은 잘 안쓰는 join에 대해서 다시 떠오르게 되었다.<br>
3.Chat GPT가 알려주는 내용을 너무 맹신하지 말자. 내가 더 정확한 경우도 있다.<br>
문제를 풀면서 시간복잡도 상위 100안에 들었다.<br>
<img width="946" alt="스크린샷 2023-07-07 오전 4 03 48" src="https://github.com/SeoGeonhyuk/TodayILearn/assets/60954160/93da00ca-15bc-40f0-853c-925c951df96f">

