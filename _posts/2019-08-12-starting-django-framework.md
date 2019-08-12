---
title: "django 시작하기"
date: 2019-08-12 14:15:00 +0900
categories: python django
---
사실 아직까지 파이썬을 제대로 써본적이 없다. 파이썬 경험이라고는 머신러닝을 공부하면서 tensorflow 예제를 조금 살펴본 정도인데, 제대로 한번 파이썬을 익히고 경험해 보고 싶은 마음에서 장고를 배워보기로 결심했다.

학부때처럼 한 언어를 처음부터 딥하게 배우기 보다는, 기본적인 문법을 짧게(1시간정도) 익히고, 그 언어의 인기있는 프레임워크를 직접 한번 설치해서 써보는 방법이 언어를 처음 배울때 가장 효과적이라 생각한다. 이미 여러 언어의 웹프레임워크를 익혀놓은 상태이기 때문에, 다른 프레임워크와 기능 하나하나를 비교해가면서 장고는 어떻게 이 기능을 제공할까 생각하면서 익히면 효율적으로 언어를 익힐수 있다고 생각한다.

가장 많이 다뤄본 라라벨과 expressjs를 기준으로 비교해보며 진행해 보았다.

우선은 설치 및 앱 작성 방법을 공식문서의 [튜토리얼](https://docs.djangoproject.com/ko/2.2/intro/)의 앞부분을 따라가 보며 알아보고, 바로 [토픽별](https://docs.djangoproject.com/ko/2.2/topics/)로 딥하게 공부해 볼 예정이다.

토픽별로 살펴볼 우선순위를 아래와 같이 정해보았다. 각각의 공식 문서를 링크하고 있다.

1. [Installation](https://docs.djangoproject.com/en/2.2/topics/install/)
2. [Handling HTTP requests](https://docs.djangoproject.com/ko/2.2/topics/http/)
    1. controller, route
    2. request, response
    3. middleware
    4. session
3. [Working with forms](https://docs.djangoproject.com/en/2.2/topics/forms/)
4. [Models and databases](https://docs.djangoproject.com/en/2.2/topics/db/)

필수적인 토픽을 우선순위를 높게 두었다. 가끔 사용하는 파일업로드, 다운로드 같은 토픽은 그때그때 필요할 때 보면 될거같고, 요즘은 SPA 환경에서 주로 API서버로 django를 사용할 것이므로 템플릿도 우선순위를 낮게두고 살펴볼 예정이다.

