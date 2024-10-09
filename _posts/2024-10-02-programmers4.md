---
layout: post
title: 프로그래머스 Lv. 0 '최빈값 구하기'
date: 2024-10-02
description: 해시 맵, 이터레이터를 이용해 풀이
tags: C++/Cpp 1주차
categories: 프로그래머스
---

## 문제 설명
---
최빈값은 주어진 값 중에서 가장 자주 나오는 값을 의미합니다. 정수 배열 array가 매개변수로 주어질 때, 최빈값을 return 하도록 solution 함수를 완성해보세요. 최빈값이 여러 개면 -1을 return 합니다.<br><br>

### 제한사항
---
- 0 < array의 길이 < 100
- 0 ≤ array의 원소 < 1000<br><br>

### 풀이 코드
---
```cpp
#include <vector>
#include <unordered_map>
using namespace std;

int solution(vector<int> array)
{
    unordered_map<int, int> umap; // 해쉬 맵
    int max, maxV = 0; // 최빈값 pair의 first, second

    // 빈도 업데이트
    for (int i = 0; i < array.size(); i++) umap[array[i]]++;

    // 이터레이터로 순회하며 최빈값 업데이트
    for (auto iter : umap) {
        if (iter.second > maxV) {
            maxV = iter.second;
            max = iter.first;
        }
        else if (iter.second == maxV) {
            max = -1;
        }
    }

    return max;
}
```

#### unordered_map, 해쉬 맵
unordered_map은 key, value 형태로 탐색하는 해쉬 맵 자료구조이다. map은 O(log n)이고, unordered_map은 O(1)이다.<br>
#include<unordered_map>을 선언하고 사용해야 하며, []연산자로 key로 value를 검색 가능하다. key가 유사한 데이터가 많으면 충돌할 가능성이 있어 주의 필요.