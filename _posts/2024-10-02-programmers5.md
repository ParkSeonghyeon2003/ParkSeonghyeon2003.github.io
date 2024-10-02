---
layout: post
title: 프로그래머스 Lv. 0 '문자열 뒤집기'
date: 2024-10-02
description: reverse_iterator로 역순회하기
tags: C++/Cpp
categories: 프로그래머스
---

## 문제 설명
---
문자열 my_string이 매개변수로 주어집니다. my_string을 거꾸로 뒤집은 문자열을 return하도록 solution 함수를 완성해주세요.<br><br>

### 제한사항
---
- 1 ≤ my_string의 길이 ≤ 1,000<br><br>

### 풀이 코드
---
```cpp
#include <string>
using namespace std;

string solution(string str)
{
	string answer = "";
	// iterator를 사용해 역으로 문자열 순회 가능.
	for (auto it = str.rbegin(); it != str.rend(); it++) answer += *it;
	return answer;
}
```

#### rbegin(), rend()
reverse_iterator는 역방향 이터레이터로, rbegin(), rend()로 마지막 원소부터 첫 원소까지를 for문을 통해 순회가 가능하다.