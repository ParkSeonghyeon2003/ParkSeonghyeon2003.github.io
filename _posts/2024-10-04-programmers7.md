---
layout: post
title: 프로그래머스 Lv. 0 '배열 자르기'
date: 2024-10-04
description: vector의 일부/전체를 다른 vector로 복사하기
tags: C++/Cpp 2주차
categories: 프로그래머스
---

## 문제 설명
---
&emsp;정수 배열 `numbers`와 정수 `num1`, `num2`가 매개변수로 주어질 때, `numbers`의 `num1`번 째 인덱스부터 `num2`번째 인덱스까지 자른 정수 배열을 return 하도록 solution 함수를 완성해보세요.<br><br>

### 제한사항
---
- 2 ≤ `numbers`의 길이 ≤ 30
- 0 ≤ `numbers`의 원소 ≤ 1,000
- 0 ≤ `num1` < `num2` < `numbers`의 길이<br><br>

### 풀이 코드
---
```cpp
#include <vector>
using namespace std;

vector<int> solution(vector<int> numbers, int num1, int num2)
{
	vector<int> answer(numbers.begin() + num1, numbers.begin() + num2 + 1);
	return answer;
}
```
&emsp;이 문제를 처음 해결했을 때, for문으로 `numbers`의 `num1`부터 `num2`번 째 인덱스의 값을 순회하며, 새로운 `vector`에 `push_back`으로 추가해줬었다.<br>
&emsp;그러나 더욱 간단한 방법이 있는데, 위 소스 코드처럼 `vector`의 생성자로 벡터를 생성할 때 `numbers`를 잘라서 복사할 수 있다. 생성자의 첫 번째 인자로 복사 시작 원소를 가르키는 iterator 개체를, 두 번째 인자로 복사 마지막 원소의 다음 원소를 가르키는 iterator 개체를 넘겨주면 된다!