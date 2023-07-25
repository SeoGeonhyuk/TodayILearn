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
# 2023.07.15
오늘은 [백준 2609번 최대공약수와 최소공배수](https://www.acmicpc.net/problem/2609), [백준 1436번 영화감독 숌](https://www.acmicpc.net/problem/1436), [백준 9012번 괄호](https://www.acmicpc.net/problem/9012) 문제를 풀었다.<br>
# 2023.07.16
오늘은 [백준 10814번 나이순 정렬](https://www.acmicpc.net/problem/10814), [백준 1966번 프린터 큐](https://www.acmicpc.net/problem/1966) 문제를 풀었다.<br>
# 2023.07.17
오늘은 [백준 10773번 제로](https://www.acmicpc.net/problem/10773) 문제를 풀었다.<br>
또한, pintos project1과 project2를 일부 구현하였다.<br>
# 2023.07.18
오늘은 [백준 1500번 최대 곱](https://www.acmicpc.net/problem/1500), [백준 1629번 곱셈](https://www.acmicpc.net/problem/1629) 문제를 풀었다.<br>
백준 1629번 곱셈 문제를 풀면서 파이썬 내부의 pow함수를 통해 기본적인 **연산을 할때의 시간복잡도 O(N)보다 더 빠른 O(logN)으로 최적화 할 수 있다는 것을 알았다.<br>
추가적으로 나머지 파라미터도 넣어지면 그 나머지 계산을 최적화하여 제곱 후 최종적인 나머지까지 빠르게 도출해 준다고 한다.<br>
하지만 이러한 기능에 의지하지 않고 직접 구현을 통해 분할정복을 통한 거듭제곱의 원리를 확실히 깨우처야겠다고 생각했다.<br>
# 2023.07.19
오늘은 [백준 1427번 소트인사이드](https://www.acmicpc.net/problem/1427), [백준 1699번 제곱수의 합](https://www.acmicpc.net/problem/1699) 문제를 풀었다.<br>
그리고 목표했던 골드티어에 진입하였다.<br>
<img width="1425" alt="스크린샷 2023-07-19 오후 12 36 08" src="https://github.com/SeoGeonhyuk/TodayILearn/assets/60954160/ced1447b-8b0b-401e-8ed6-7c28859194a1">
## 앞으로의 계획
프로그래머스 쪽으로 넘어가서 자료구조에 관련된 문제를 풀 계획이다.<br>
# 2023.07.20
프로그래머스 스택/큐 부분 2문제를 풀었다.<br>
추가적으로 웹개발 공부를 진행하였다.<br>
# 2023.07.21
오늘은 프로그래머스 레벨2 한 문제를 풀었다.<br>
# 2023.07.23
오늘은 프로그래머스 레벨 2 한 문제를 풀었다.<br>
# 2023.07.24
오늘은 프로그래머스 레벨 2 한 문제를 풀었다.<br>
문제를 풀면서 정렬을 하는 기준인 key에 대해서 lambda를 이용하여 key를 정의하고 정렬하는 법을 깨달았다.<br>
하지만 익숙해지는데는 시간이 필요할 것 같다.<br>
# 2023.07.25
오늘은 웹개발 공부를 진행하였다.<br>
공부를 하며 dom이 무엇이고 dom에 있는 여러 객체들을 querySelector를 통해서 조정하는 법을 알았다.<br>
