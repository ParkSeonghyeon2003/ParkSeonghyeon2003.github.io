---
layout: post
title: 프로그래머스 Lv. 0 '두 수의 나눗셈'
date: 2024-10-02
description: 명시적/묵시적 타입캐스팅을 이용해 풀이
tags: C++/Cpp 1주차
categories: 프로그래머스
---

## 문제 설명
---
정수 num1과 num2가 매개변수로 주어질 때, num1을 num2로 나눈 값에 1,000을 곱한 후 정수 부분을 return 하도록 soltuion 함수를 완성해주세요.<br><br>

### 제한사항
---
- 0 < num1 ≤ 100
- 0 < num2 ≤ 100<br><br>

### 풀이 코드
---
```cpp
int solution(int num1, int num2) {
    return (double)num1 / num2 * 1000;
}
```
정수끼리의 나눗셈을 위해 `(double)`로 타입캐스팅 후 `/`으로 연산한다. 수식 결과값을 return 할 때, <u>**암묵적**</u>으로 `int`형으로 타입캐스팅 된다. 이렇게 하면 정수 부분 만 구할 수 있다!
