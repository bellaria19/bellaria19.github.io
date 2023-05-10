---
layout: post
title:  "Python Regex2"
date:   2023-05-09 13:30:00 +0900
categories: study
---
지난번에 사용한 정규식에서 이번에는 re에 정의된 것을 사용하는 문제를 풀어본다.

정규식에 해당되는 지 안되는 지를 판별하는 것이다.

Sample Input
```
2
.*\+
.*+
```

Sample Output
```
True
False
```
들어온 입력을 정규표현식인지 판단해 True, False로 출력하면된다.

re.compile(pattern)을 사용하면 pattern이 정규 표현식이면 정규식 객체로 컴파일하고 아니면 실패합니다.
그러므로 입력이 정규 표현식이면 컴파일에 성공하고 아니면 실패하는 것이다.
try-except문을 사용해 성공하면 true를 출력, 실패하면 false를 출력한다.


{% highlight python %}

try:
    m = re.compile(input)
    print(True)
except:
    print(False)

{% endhighlight %}


[HackerRank][HackerRank] 
[Problem][Problem]


[HackerRank]: https://www.hackerrank.com/
[Problem]: https://www.hackerrank.com/challenges/incorrect-regex/problem