---
layout: post
title:  "Python Regex + email"
date:   2023-04-08 15:37:00 +0900
categories: study
---
수업에서 python을 사용하는데 너무 오랜만에 사용하다 보니 잘 쓰질 못해서 HackerRank에 있는 문제로 재활시작!

처음으로 email을 사용하는 문제를 보게됬는데 email.utils를 사용하면 된다고 한다.

{% highlight ruby %}

import email.utils

print email.utils.parseaddr('DOSHI <DOSHI@hackerrank.com>')
print email.utils.formataddr(('DOSHI', 'DOSHI@hackerrank.com'))

{% endhighlight %}

parseaddr은 입력을 공백을 기준으로 나누어 튜플을 반환하는데 실패하면 ('', '')으로 반환된다.
"DOSHI <DOSHI@hackerrank.com>" 가 입력으로 주어지면 ('DOSHI',  'DOSHI@hackerrank.com')으로 만드는 것이다.

formataddr은 위 형식의 튜플을 입력으로 받아 "DOSHI <DOSHI@hackerrank.com>"로 문자열을 반환한다.


* 이메일의 첫 문자는 알파벳으로 시작한다.
* 이어진 문자열은 알파벳과 숫자, -, ., _로 구성되어 있다.
* 도메인과 확장자는 오직 알파벳으로 이루어져 있다.
* 확장자의 길이는 1, 2, 3이다.



|---|:-----------|:------|
|+|1개 이상|
|*|0개 이상|
|{}|길이 지정|
|[]|범위 지정|
|\d|[0-9]|숫자|
|\D|[^0-9]|비 숫자|
|\s|[\t\n\r\f\v]|공백 문자|
|\S|[^\t\n\r\f\v]|비 공백 문자|
|\w|[a-zA-Z0-9_]|모든 영숫자|
|\W|[^a-zA-Z0-9_]|모든 비 영숫자|


첫 문자는 알파벳이므로 [a-zA-Z] 뒤에 붙는 문자열은 [\w.-] 도메인과 확장자는 [a-zA-Z] 확장자의 길이는 1~3이므로 {1,3}

{% highlight ruby %}

[a-zA-Z][\w.-]+@[a-zA-Z]+\.[a-zA-Z]{1,3}

{% endhighlight %}


[HackerRank][HackerRank] 
[Problem][Problem]


[HackerRank]: https://www.hackerrank.com/
[Problem]: https://www.hackerrank.com/challenges/validating-named-email-addresses/problem