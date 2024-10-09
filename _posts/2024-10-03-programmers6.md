---
layout: post
title: 프로그래머스 Lv. 0 '특정 문자 제거하기'
date: 2024-10-03
description: 길이가 1인 string형 변수를 char형 변수와 비교하기
tags: C++/Cpp 2주차
categories: 프로그래머스
---

## 문제 설명
---
&emsp;문자열 `my_string`과 문자 `letter`이 매개변수로 주어집니다. `my_string`에서 `letter`를 제거한 문자열을 return하도록 solution 함수를 완성해주세요.<br><br>

### 제한사항
---
- 1 ≤ `my_string`의 길이 ≤ 100
- `letter`은 길이가 1인 영문자입니다.
- `my_string`과 `letter`은 알파벳 대소문자로 이루어져 있습니다.
- 대문자와 소문자를 구분합니다.<br><br>

### 풀이 코드
---
```cpp
#include <string>
using namespace std;

string solution(string my_string, string letter) {
	string answer = "";
	for (auto& chr : my_string) // iterator 순회. chr는 char&형이 됨.
		if (chr != letter[0]) answer += chr; // letter가 아니면 answer에 추가
	return answer;
}
```
&emsp;`string` 변수를 iterator와 for문으로 순회하면, 값의 타입이 `char`이다. 허나 매개변수로 `letter`를 `string`형으로 받기 때문에 비교 연산을 할 수 없다.<br>
&emsp;비교 연산을 하기 위해서 `c_str()`같은 라이브러리 함수를 사용하기 보다는, letter의 길이가 1이라는 제한 사항을 참고하고, `char&`를 반환하는 []오퍼레이터를 사용하여 `letter[0]`와 같이 써주면 간단히 해결된다.