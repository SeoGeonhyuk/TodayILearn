# TodayILearn
2023-1학기 여름방학 모각소를 위한 TIL 레포지토리<br>
https://github.com/SeoGeonhyuk/Backjoon.git<br>
기본적으로 모든 문제 풀이 코드는 위 링크의 깃허브에 커밋하고 있습니다.<br>
# 2023.07.05
백준 6064번 문제<br>
https://www.acmicpc.net/problem/6064<br>
중국인의 나머지 정리 공부<br>
유클리드 호제법을 이용할 경우 최대공약수를 쉽게 구할 수 있다.<br>
파이썬을 이용하여 코드를 작성할 경우 다음과 같다.<br>
\\\
def gcd(a, b):
    if b == 0:
        return a
    else:
        return gcd(b, a % b)
\\\
이 호제법에서는 특정한 법칙이 적용되는데 이에 대한 법칙 3가지는 다음과 같다.<br>
1. gcd(a, b) = gcd(b, a)<br>
2. gcd(a, 0) = a<br>
3. gcd(a, b) = gcd(a (mod b), b)<br>
