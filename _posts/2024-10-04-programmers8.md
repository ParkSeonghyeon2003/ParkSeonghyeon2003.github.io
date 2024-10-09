---
layout: post
title: 프로그래머스 Lv. 0 '외계행성의 나이'
date: 2024-10-04
description: int를 string으로 변환하는 to_string() 함수와 char 변수의 정수 연산
tags: C++/Cpp 2주차
categories: 프로그래머스
---

## 문제 설명
---
&emsp;우주여행을 하던 머쓱이는 엔진 고장으로 PROGRAMMERS-962 행성에 불시착하게 됐습니다. 입국심사에서 나이를 말해야 하는데, PROGRAMMERS-962 행성에서는 나이를 알파벳으로 말하고 있습니다. a는 0, b는 1, c는 2, ..., j는 9입니다. 예를 들어 23살은 cd, 51살은 fb로 표현합니다. 나이 `age`가 매개변수로 주어질 때 PROGRAMMER-962식 나이를 return하도록 solution 함수를 완성해주세요.<br><br>

### 제한사항
---
- `age`는 자연수입니다.
- `age` ≤ 1,000
- PROGRAMMERS-962 행성은 알파벳 소문자만 사용합니다.<br><br>

### 풀이 코드
---
```cpp
#include <string>
using namespace std;

string solution(int age) {
    string answer = to_string(age);
    for (auto& chr : answer) chr += 'a' - '0';
    return answer;
}
```
&emsp;`to_string()`함수는 string 라이브러리 함수로, 인자로 받은 수를 `string` 문자열로 반환한다.<br>
&emsp;또한, 한 자리 수의 `int` 변수는 `'0'`을 빼고, `'a'`를 더한 다음 `char`형 변수에 배정하는 과정에서, `char`형으로 암묵적으로 캐스팅되므로, 어떤 라이브러리 함수 없이도 정수를 문자로 변환할 수 있다.