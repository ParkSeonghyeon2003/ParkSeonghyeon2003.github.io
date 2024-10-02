---
layout: post
title: 프로그래머스 Lv. 0 '분수의 덧셈'
date: 2024-10-02
description: 유클리드 호제법을 이용해 풀이
tags: C++/Cpp
categories: 프로그래머스
---

## 문제 설명
---
첫 번째 분수의 분자와 분모를 뜻하는 numer1, denom1, 두 번째 분수의 분자와 분모를 뜻하는 numer2, denom2가 매개변수로 주어집니다. 두 분수를 더한 값을 기약 분수로 나타냈을 때 분자와 분모를 순서대로 담은 배열을 return 하도록 solution 함수를 완성해보세요.<br><br>

### 제한사항
---
- 0 < numer1, denom1, numer2, denom2 < 1,000<br><br>

### 풀이 코드
---
```cpp
#include <vector>
using namespace std;

// 유클리드 호제법
int gcd(int a, int b) {
    int r;
    int bigger = a >= b ? a : b;
    int smaller = a < b ? a : b;
    while (smaller != 0) {
        r = bigger % smaller;
        bigger = smaller;
        smaller = r;
    }
    return bigger;
}

vector<int> solution(int numer1, int denom1, int numer2, int denom2) {
    vector<int> answer(2);
    int numer = numer1 * denom2 + numer2 * denom1; // 통분
    int denom = denom1 * denom2; // 통분

    int gcdV = gcd(numer, denom); // 최대공약수 구하기

    answer[0] = numer / gcdV; answer[1] = denom / gcdV; // 최대공약수로 기약분수 만들기
    return answer;
}
```

#### 유클리드 호제법
2개의 자연수(또는 정식) a, b에 대해서 a를 b로 나눈 나머지를 r이라 하면(단, a>b), a와 b의 최대공약수는 b와 r의 최대공약수와 같다. 이 성질에 따라, b를 r로 나눈 나머지 r'를 구하고, 다시 r을 r'로 나눈 나머지를 구하는 과정을 반복하여 나머지가 0이 되었을 때 나누는 수가 a와 b의 최대공약수이다.<br>
[유클리드 호제법 - Wikipedia](https://ko.wikipedia.org/wiki/%EC%9C%A0%ED%81%B4%EB%A6%AC%EB%93%9C_%ED%98%B8%EC%A0%9C%EB%B2%95)