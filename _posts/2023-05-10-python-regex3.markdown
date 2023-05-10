---
layout: post
title:  "Python Regex3"
date:   2023-05-10 13:00:00 +0900
categories: study
---
이어서 정규식과 파싱을 통해 색상의 hex값만을 찾아내는 문제이다.

입력으로 들어온 문자열에서 필요없는 문자들은 버리고 제대로된 hex값 표기를 지키는 값만 파싱하는 것이다. 

Examples:
```
Valid Hex Color Codes
#FFF 
#025 
#F0A1FB 

Invalid Hex Color Codes
#fffabg
#abcf
#12365erff
```
hex값은 0 ~ 9와 대소문자 A ~ F까지만 사용하고 3자리 또는 6자리로 표현한다.

입력은 CSS 코드의 형식으로 들어온다.

Sample Input
```
#BED
{
    color: #FfFdF8; background-color:#aef;
    font-size: 123px;
    background: -webkit-linear-gradient(top, #f9f9f9, #fff);
}
#Cab
{
    background-color: #ABC;
    border: 2px dashed #fff;
}
```

Sample Output
```
#FfFdF8
#aef
#f9f9f9
#fff
#ABC
#fff
```

hex값의 형식을 pattern, 구분을 위한 문자를 character로 정규식 표현을 저장한다.
```

pattern = r'^#([0-9a-fA-F]{3}|[0-9a-fA-F]{6})$'
character = r'[^\w\{\}#]'

```

CSS는 '{'로 시작해 '}'로 끝나므로 '{'만났을 떄 파싱한 문자들을 탐색하며 패턴과 일치하는 문자를 결과에 저장한다. '}'을 만나면 저장하지 않는다.

```

line = sys.stdin.readline()
line = re.sub(character, ' ', line).split(' ')

for i in line:
    if get_color:
        if re.match(pattern, i):
            res.append(i)

```

re.sub(pattern, repl, string)
string에서 pattern에 해당되지 않는 것을 repl로 치환하여 문자열을 반환하는 것이다.

re.match(pattern, string)
string이 pattern과 일치하면 일치 객체(Match Objects)를 반환하고 다르면 None을 반환한다. 따라서 if문으로 비교가능하다.




[HackerRank][HackerRank] 
[Problem][Problem]


[HackerRank]: https://www.hackerrank.com/
[Problem]: https://www.hackerrank.com/challenges/hex-color-code/problem