---
layout: post
title: 프로그래머스 Lv. 0 '모스부호 (1)'
date: 2024-10-05
description: 모스부호 해독하기
tags: C++/Cpp 2주차
categories: 프로그래머스
---

## 문제 설명
---
&emsp;머쓱이는 친구에게 모스부호를 이용한 편지를 받았습니다. 그냥은 읽을 수 없어 이를 해독하는 프로그램을 만들려고 합니다. 문자열 `letter`가 매개변수로 주어질 때, `letter`를 영어 소문자로 바꾼 문자열을 return 하도록 solution 함수를 완성해보세요.
모스부호는 다음과 같습니다.<br>
```
morse = { 
    '.-':'a','-...':'b','-.-.':'c','-..':'d','.':'e','..-.':'f',
    '--.':'g','....':'h','..':'i','.---':'j','-.-':'k','.-..':'l',
    '--':'m','-.':'n','---':'o','.--.':'p','--.-':'q','.-.':'r',
    '...':'s','-':'t','..-':'u','...-':'v','.--':'w','-..-':'x',
    '-.--':'y','--..':'z'
}
```
<br><br>

### 제한사항
---
- 1 ≤ `letter`의 길이 ≤ 1,000
- return값은 소문자입니다.
- `letter`의 모스부호는 공백으로 나누어져 있습니다.
- `letter`에 공백은 연속으로 두 개 이상 존재하지 않습니다.
- 해독할 수 없는 편지는 주어지지 않습니다.
- 편지의 시작과 끝에는 공백이 없습니다.<br><br>

### 풀이 코드
---
```cpp
#include <string>
using namespace std;

string solution(string letter)
{
    int i, strLen = letter.length();
    string answer = "";
    string temp = "";
    string morse[] = {
        ".-","-...","-.-.","-..",
        ".","..-.","--.","....",
        "..",".---","-.-",".-..",
        "--","-.","---",".--.",
        "--.-",".-.","...","-",
        "..-","...-",".--","-..-",
        "-.--","--.."
    };
    for (int idx = 0; idx < strLen; idx++) {
        if (idx == strLen - 1) temp += letter[idx];
        if (letter[idx] == ' ' || idx == strLen - 1) {
            for (i = 0; i < 26; i++) {
                if (morse[i] == temp) break;
            }
            answer += i + 'a';
            temp = "";
            continue;
        }
        temp += letter[idx];
    }
    return answer;
}
```
&emsp;`string`형 변수 `temp`를 선언해, 공백을 만나지 않았다면, `temp`에 모스부호 문자를 추가한다.<br>
&emsp;공백을 만나게 되거나, 마지막 모스부호 문자를 만나게 되면, `temp`가 모스부호 사전에서 몇 번째 인덱스의 문자열과 같은지를 검사하여, 해당 인덱스값과 `'a'`를 더하여 `answer`에 더하면, 모스부호가 해독된 문자열이 완성된다.<br>
&emsp;뭔가 더 깔끔하게 코딩할 수 있을 것 같다...