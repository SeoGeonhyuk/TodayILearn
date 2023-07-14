# TodayILearn
2023-1학기 여름방학 모각소를 위한 TIL 레포지토리<br>
기본적으로 모든 문제 풀이 코드들은 따로 [전용 깃허브](https://github.com/SeoGeonhyuk/Backjoon.git)에 커밋하고 있습니다.<br>
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
    for i in vertex[start]: #vertex는 각 원소타입이 list인 list이다. 여기에는 간선의 정보가 있다.
        if not BFSListVisited[i]:
            BFSListVisited[i] = True
            BFSList.append(i)
```
## DFS
```
DFS = []
DFSList = [s[2]]
DFSListVisited = [False] * (s[0] + 1)
DFST(DFS, DFSList, DFSListVisited, vertex) #vertex는 각 원소타입이 list인 list이다. 여기에는 간선의 정보가 있다.
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
[백준 6064번 카잉 달력](https://www.acmicpc.net/problem/6064) 문제를 풀었다<br>
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
[백준 1260번 DFS와 BFS](https://www.acmicpc.net/problem/1260)를 풀면서 느낀점<br>
1.최적화하는 방법은 무궁무진하게 많다.<br>
2.예전에만 쓰고 지금은 잘 안쓰는 join에 대해서 다시 떠오르게 되었다.<br>
3.Chat GPT가 알려주는 내용을 너무 맹신하지 말자. 내가 더 정확한 경우도 있다.<br>
문제를 풀면서 시간복잡도 상위 100안에 들었다.<br>
<img width="946" alt="스크린샷 2023-07-07 오전 4 03 48" src="https://github.com/SeoGeonhyuk/TodayILearn/assets/60954160/93da00ca-15bc-40f0-853c-925c951df96f"><br>
추가로 [백준 1764번 듣보잡](https://www.acmicpc.net/problem/1764) 문제도 풀었다.<br>
# 2023.07.08
오늘은 [백준 11047번 동전 0](https://www.acmicpc.net/problem/11047), [백준 2606번 바이러스](https://www.acmicpc.net/problem/2606) 문제를 풀었다.<br>
문제를 풀면서 느낀 점<br>
1.구현에 집중하지 말고 시간복잡도를 최적화하는데 집중하라<br>
# 2023.07.09 ~ 10
pintos project1 구현작업을 진행했다.<br>
# 2023.07.11
교수님과 학부 인턴 미팅을 하면서 pintos내에서 인터럽트를 끄고 켰을 떄의 레이턴시가 증가하면 어떻게 되는지 배웠다.<br>
기본적으로 인터럽트를 끄고 켰을 때의 레이턴시가 크개 발생하면 기존 상태에서 잘 작동해야 하는 인터럽트를 제대로 처리하지 못하고 그대로 인터럽트를 생략한다.<br>
물론 인터럽트를 받지 않게 처리하였을 때 이러한 인터럽트를 보관하는 pending 인터럽트 항목이 존재하지만 이런 pending 인터럽트에 속하지 못하는 인터럽트는 그대로 생략된다.<br>
예시로 이러한 현상으로 인해 타이머 인터럽트가 무시되어 후에 타이머 관련 인터럽트를 처리할 때 문제가 발생할 수 있다.<br>
추가적으로 semaphore, lock 뿐만 아니라 이를 활용한 monitor 동기화에 대해서도 배웠다.<br>
# 2023.07.12
[백준 11723번 집합](https://www.acmicpc.net/problem/11723), [백준 11399번 ATM](https://www.acmicpc.net/problem/11399), [백준 10989번 수 정렬하기 3](https://www.acmicpc.net/problem/10989) 문제를 풀었다.<br>
# 2023.07.13
[백준 9095번 1,2,3 더하기](https://www.acmicpc.net/problem/9095) 문제를 풀었다.
## 느낀 점
DP에 대한 경험이 좀 더 필요하다고 생각했다. DP 관련 문제를 많이 풀어보아야 할 것 같다.
## 피사노 주기(Pisano period)
피보나치 수를 어떤 수 K로 나눌 때, 나머지는 항상 주기를 가지게 되는데 이를 피사노 주기라고 한다.<br>
성질:주기의 길이를 P라고 하면 N번째 피보나치 수를 M으로 나눈 나머지는 N%P번째 피보나치 수를 M으로 나눈 나머지와 같다.<br>
주기 P는 M = 10^k(k>2)의 형식일 경우, 항상 P = 15 * 10 ^ (k-1)이다<br>
# 2023.07.14
오늘은 [백준 12101번 1,2,3 더하기 2](https://www.acmicpc.net/problem/12101) 문제를 풀었다.<br>
## 느낀 점
확실히 지금 나는 DP에 대해서 익숙치 않은 상태인거 같다. 당분간 DP에 대해서 집중적으로 공부해야겠다.<br>
