---
layout: post
title: 프로그래머스 Lv. 0 '숫자 비교하기'
date: 2024-10-02
description: 삼항연산자를 이용해 풀이
tags: C++/Cpp
categories: 프로그래머스
---

## 문제 설명
---
정수 num1과 num2가 매개변수로 주어집니다. 두 수가 같으면 1 다르면 -1을 retrun하도록 solution 함수를 완성해주세요.<br><br>

### 제한사항
---
- 0 ≤ num1 ≤ 10,000
- 0 ≤ num2 ≤ 10,000<br><br>

### 풀이 코드
---
```cpp
int solution(int num1, int num2) {
    return num1 == num2 ? 1 : -1; // 삼항연산자 사용
}
```

#### 삼항연산자
삼항연산자는 `A (조건) B ? C : D;`의 형태로 나타내며, 왼쪽 조건 식을 만족하면 C, 만족하지 못하면 D를 반환한다.
