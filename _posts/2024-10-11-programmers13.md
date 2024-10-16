---
layout: post
title: 프로그래머스 Lv. 0 '영어가 싫어요'
date: 2024-10-11
description: string::find, string::replace, std::atoll
tags: C++/Cpp 3주차
categories: 프로그래머스
---

## 문제 설명
---
&emsp;영어가 싫은 머쓱이는 영어로 표기되어있는 숫자를 수로 바꾸려고 합니다. 문자열 `numbers`가 매개변수로 주어질 때, `numbers`를 정수로 바꿔 return 하도록 solution 함수를 완성해 주세요.<br><br>

### 제한사항
---
- `numbers`는 소문자로만 구성되어 있습니다.
- `numbers`는 "zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine" 들이 공백 없이 조합되어 있습니다.
- 1 ≤ `numbers`의 길이 ≤ 50
- "zero"는 `numbers`의 맨 앞에 올 수 없습니다.<br><br>

### 풀이 코드
---
```cpp
#include <string>
#include <vector>

using namespace std;

typedef long long ll;

vector<string> dict {
    "zero", "one", "two", "three",
    "four", "five", "six", "seven",
    "eight", "nine"
};

ll solution(string numbers)
{
    ll answer = 0;
    for (int i = 0; i < dict.size(); i++)
    {
        size_t pos;
        while (string::npos != (pos = numbers.find(dict[i])))
        {
            numbers.replace(pos, dict[i].length(), to_string(i));
        }
    }
    answer = atoll(numbers.c_str());
    return answer;
}
```
&emsp;`string::find`는 `string` 문자열에서 특정 `string` 문자열을 찾아, 시작 위치를 반환하고, 만약 없으면 `string::npos`를 반환한다.<br>
&emsp;`string::replace`는 시작 위치, 길이, 바꿀 문자열을 인자로 받아 그 위치에 맞게 문자열을 재배치한다.<br>
&emsp;`std::atoll`는 `std::atoi`와 마찬가지로 `char *`형 변수를 `long long` 타입으로 변환시켜준다. 위 코드에서는 `string`인 `numbers`를 `string::c_str`함수로 `char *`타입으로 변환한 후 `std::atoll`로 또 변환해주었다.