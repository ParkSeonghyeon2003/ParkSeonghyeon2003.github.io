---
layout: post
title: 프로그래머스 Lv. 0 '구슬을 나누는 경우의 수'
date: 2024-10-05
description: 수학의 조합 개념을 이용한 풀이
tags: C++/Cpp 2주차
categories: 프로그래머스
---

## 문제 설명
---
&emsp;머쓱이는 구슬을 친구들에게 나누어주려고 합니다. 구슬은 모두 다르게 생겼습니다. 머쓱이가 갖고 있는 구슬의 개수 `balls`와 친구들에게 나누어 줄 구슬 개수 `share`이 매개변수로 주어질 때, `balls`개의 구슬 중 `share`개의 구슬을 고르는 가능한 모든 경우의 수를 return 하는 solution 함수를 완성해주세요.<br><br>

### 제한사항
---
- 1 ≤ `balls` ≤ 30
- 1 ≤ `share` ≤ 30
- 구슬을 고르는 순서는 고려하지 않습니다.
- `share` ≤ `balls`<br><br>

### 풀이 코드
---
```cpp
using namespace std;

long long solution(int balls, int share)
{
    double answer = 1;
    for (int i = balls-share + 1; i <= balls; i++) {
        answer *= i;
    }
    for (int i = 2; i <= share; i++) {
        answer /= i;
    }
    return answer;
}
```
&emsp;수학의 조합 개념을 도입하면 쉽게 해결 가능하다. n개 중 r개를 뽑는 경우의 수는 `n!/((n-r)!m!)`이다. 보통 계산할 때, 약분을 통해 `((n-r)*...*n) / (1*...*r)`으로 계산한다. 이를 for문으로 구현하면 위처럼 구현하게 된다.