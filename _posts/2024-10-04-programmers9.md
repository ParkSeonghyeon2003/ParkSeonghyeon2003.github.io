---
layout: post
title: 프로그래머스 Lv. 0 '진료 순서 정하기'
date: 2024-10-04
description: pair 클래스와 sort() 함수로 해결
tags: C++/Cpp 2주차
categories: 프로그래머스
---

## 문제 설명
---
&emsp;외과의사 머쓱이는 응급실에 온 환자의 응급도를 기준으로 진료 순서를 정하려고 합니다. 정수 배열 `emergency`가 매개변수로 주어질 때 응급도가 높은 순서대로 진료 순서를 정한 배열을 return하도록 solution 함수를 완성해주세요.<br><br>

### 제한사항
---
- 중복된 원소는 없습니다.
- 1 ≤ `emergency`의 길이 ≤ 10
- 1 ≤ `emergency`의 원소 ≤ 100<br><br>

### 풀이 코드
---
```cpp
#include <vector>
#include <algorithm>
using namespace std;

bool compare(pair<int, int> a, pair<int, int> b)
{
    return a.second > b.second;
}

vector<int> solution(vector<int> emergency) {
    vector<int> answer(emergency.size());
    vector<pair<int, int>> v;
    for (int i = 0; i < emergency.size(); i++) {
        pair<int, int> temp;
        temp.first = i;
        temp.second = emergency[i];
        v.push_back(temp);
    }
    sort(v.begin(), v.end(), compare);
    for (int i = 0; i < v.size(); i++) answer[v[i].first] = i + 1;
    return answer;
}
```
&emsp;`pair` 클래스는 `utility` 헤더 파일에 존재한다. `vector` 헤더에 `utility` 헤더 파일이 포함된다.<br>
&emsp;`algorithm` 헤더 파일에 있는 `sort()` 함수를 사용하면, `vector<pair<int, int>>`형 변수를 정렬할 수 있다. 물론 비교를 위한 `compare` 함수를 정의하여 인자로 넘겨주어야 한다. 이 후 for문으로 정렬된 벡터를 순회하며, 몇 번째 순회인지에 따라 `answer` 벡터에 높은 응급도의 인덱스부터 값을 진료 순서로 채워간다.<br>
&emsp;다 풀고나니 `map` 자료구조로 구현하면, 뭔가 더 아름답게 구현할 수 있지않을까... 싶었다.