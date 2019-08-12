---
title: "파이썬 functools.partial 함수"
date: 2019-08-11 14:00:00 +0900
categories: python
---
python을 딥하게 공부하기 위한 목적으로 django를 보고 있다. `django.urls`의 `path` 함수의 시그니처가 궁금하여 살펴보다가 아래 구문을 발견했다.


`path = partial(_path, Pattern=RoutePattern)`

뭐지? `partial`은 무슨 함수지? 다른 언어에서 보지못한 생소한 느낌이다. 그래서 한번 살펴보았다.

개념은 간단하다. 단순히 기존의 함수와 구현은 동일하고 파라메터만 미리 정해준 또 다른 함수를 생성한다.

아래 예를 보자.

```
from functools import partial

def power(base, exponent):
    return base ** exponent
```

`power`는 밑이 `base`인 수의 지수(exponent)승를 반환하는 함수이다.

이때 만약 특정 정사각형의 면적을 구하는 함수 `square`를 구현하고 싶다면?

```py
def square(arm):
    return arm ** 2
```
위와 같이 구현하면 된다. 이때 power 함수를 재사용할 수 있다.

```py
square = partial(power, exponent=2)
```

더 심플하다.

단순히 파라메터만 미리 지정해준다. 함수 오버로딩, 오버라이딩 개념과는 상관없고, 객체지향의 trait처럼 구현을 재사용하는 개념과 비슷하다. 단, 대상이 함수라는 것.

http://www.incodom.kr/%ED%8C%8C%EC%9D%B4%EC%8D%AC/%ED%95%A8%EC%88%98 에도 잘 설명되어 있지만 조금 딥하다. 나중에 더 파봐야할듯!



참고: https://hamait.tistory.com/823



