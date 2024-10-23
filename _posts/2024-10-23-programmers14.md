---
layout: post
title: 프로그래머스 Lv. 0 '문자열 계산하기'
date: 2024-10-23
description: stack 자료구조로 POSTFIX 연산 수행하기
tags: C++/Cpp 4주차
categories: 프로그래머스
---

## 문제 설명
---
&emsp;`my_string`은 "3 + 5"처럼 문자열로 된 수식입니다. 문자열 `my_string`이 매개변수로 주어질 때, 수식을 계산한 값을 return 하는 solution 함수를 완성해주세요.<br><br>

### 제한사항
---
- 연산자는 +, -만 존재합니다.
- 문자열의 시작과 끝에는 공백이 없습니다.
- 0으로 시작하는 숫자는 주어지지 않습니다.
- 잘못된 수식은 주어지지 않습니다.
- 5 ≤ `my_string`의 길이 ≤ 100
- `my_string`을 계산한 결과값은 1 이상 100,000 이하입니다.
- `my_string`의 중간 계산 값은 -100,000 이상 100,000 이하입니다.
- 계산에 사용하는 숫자는 1 이상 20,000 이하인 자연수입니다.
- `my_string`에는 연산자가 적어도 하나 포함되어 있습니다.
- return type 은 정수형입니다.
- `my_string`의 숫자와 연산자는 공백 하나로 구분되어 있습니다.<br><br>

### 풀이 코드
---
```cpp
#include <string>
#include <stack>

using namespace std;

stack<int> numbers;

// Push integer parsed from string.
void parsing(const string& str)
{
    string temp = "";
    int pushElem;
    int sign = 1;
    string::const_iterator iter;
    for (iter = str.begin(); iter < str.end(); ++iter)
    {
        if (iter == str.end() - 1) temp += *iter; // last char
        // push integer when meet space or last char.
        if (*iter == ' ' || iter == str.end() - 1)
        {
            // if latest operator = '-', multiply -1.
            pushElem = atoi(temp.c_str()) * sign;
            ++iter;
            if (*iter == '-') sign = -1;
            else sign = 1;
            ++iter;
            numbers.push(pushElem);
            temp = "";
        }
        else
            temp += *iter;
    }
    return;
}

int solution(string my_string)
{
    int answer = 0;
    parsing(my_string);
    while (!numbers.empty())
    {
        answer += numbers.top();
        numbers.pop();
    }
    return answer;
}
```
&emsp;C++에 STL 라이브러리로 stack 자료구조가 구현되어 있다. POSTFIX 연산은 3 + 5 따위의 연산을 3 5 + 따위로 표기하여 피연산자를 모두 쓴 다음 연산자를 쓰는 연산법이다.<br>
&emsp;나는 문제를 풀기 위해 `my_string`을 파싱하여 피연산자를 stack에 push하였다. 3 - 5는 3 + (-5)와 같기 때문에 피연산자를 push할 때 앞 연산자가 `-`면 -1를 곱하여 부호를 `-`로 만들어서 push한다. 나중에 stack의 원소를 모두 더하면 답을 구할 수 있다.