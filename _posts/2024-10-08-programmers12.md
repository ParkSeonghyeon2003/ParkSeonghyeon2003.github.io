---
layout: post
title: 프로그래머스 Lv. 0 '소인수분해'
date: 2024-10-08
description: set으로 소인수분해하기
tags: C++/Cpp 2주차
categories: 프로그래머스
---

## 문제 설명
---
&emsp;소인수분해란 어떤 수를 소수들의 곱으로 표현하는 것입니다. 예를 들어 12를 소인수 분해하면 2 * 2 * 3 으로 나타낼 수 있습니다. 따라서 12의 소인수는 2와 3입니다. 자연수 `n`이 매개변수로 주어질 때 `n`의 소인수를 오름차순으로 담은 배열을 return하도록 solution 함수를 완성해주세요.<br><br>

### 제한사항
---
- 2 ≤ `n` ≤ 10,000<br><br>

### 풀이 코드
---
```cpp
#include <vector>
#include <set>
using namespace std;

bool isPrimeNumber(const set<int>& primeDivisor, const int& number)
{
    for (auto& it : primeDivisor) {
        if (number % it == 0) return false;
    }
    return true;
}

vector<int> solution(int n)
{
    vector<int> answer;
    set<int> primeDivisor;
    for (int i = 2; i <= n; i++) {
        if (n % i == 0 && isPrimeNumber(primeDivisor, i)) {
            primeDivisor.insert(i);
        }
    }
    answer.assign(primeDivisor.begin(), primeDivisor.end());
    return answer;
}
```
&emsp;`isPrimeNumber()`라는 함수를 만들어 이미 구한 소인수의 집합(`set`)과 소인수인지 판별할 정수를 매개변수로 받아 `set`을 iterator로 순회하며 정수를 iterator 개체의 값으로 나머지 연산하여, 나머지가 0인 순간에 바로 `false`를 반환한다.<br>
&emsp;for문으로 `n`까지의 모든 자연수중에 약수를 `isPrimeNumber()`함수의 인자로 넘겨주어 소인수의 집합을 `set`변수에 담는다. 이를 `vector`의 `assign()`함수를 통해 벡터로 변환하여 정답을 구하였다.