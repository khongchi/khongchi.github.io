---
title: "django 기본 앱 생성"
date: 2019-08-12 14:20:00 +0900
categories: python django
---
지난 글에서 django를 설치하고 첫번째 프로젝트를 생성하고, 개발 서버를 구동한 다음 웹브라우저에서 실제로 열어보는 작업까지 진행했다. 이번 글에서는 실제 원하는 앱을 직접 코딩하며 작성해보는 시간을 가지기로 하자.


# 앱 만들기

> https://docs.djangoproject.com/ko/2.2/intro/tutorial01/#creating-the-polls-app


이제 우리 프로젝트에 app을 하나 생성해보자. app은 프로젝트에서 제공하는 특정한 기능 하나라고 생각하면 되겠다. 지금까지 하나의 프로젝트에서 여러개의 앱을 돌리는 경우는 내 경우 많지 않았다. ^^

일단 튜토리얼을 따라가 보자.

`python manage.py startapp polls`

```
khongchi@MAC:~/dev/ex_django$ python3 manage.py startapp polls
khongchi@MAC:~/dev/ex_django$ tree polls/
polls/
├── __init__.py
├── admin.py
├── apps.py
├── migrations
│   └── __init__.py
├── models.py
├── tests.py
└── views.py

1 directory, 7 files
```

위 명령은 앱의 기본적인 디렉토리 구조를 만들어 준다.


# 첫번째 뷰 만들기

뷰라고 했지만 다른 MVC 프레임웍의 컨트롤러라고 보면 되겠다.

일단 컨트롤러를 만든 다음 url과 컨트롤러를 연결하는 라우트를 추가해 보자.

> laravel, expressjs에서의 route가 django에서는 url이라고 생각하면 되겠다.

### `views.py`

만들어진 app 디렉토리 안에 controllers가 없다. MVC 프레임웍 관점에서 생각하면 `views`가 controller라고 보면 되겠다. `polls/views.py`에 컨트롤러 함수 하나를 추가한다.

```py
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello, world. You're at the polls index")
```

`index`라는 컨트롤러를 추가했다. request는 인자로 받고, response는 import한 django.http의 HttpResponse를 사용했다.

### `urls.py`

라우트를 등록해보자. `polls/urls.py` 파일에 아래와 같이 작성하자.

```
from django.urls import path

from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```

`path`함수를 써서 등록했다. `path` 함수만으로는 안 되고, 이를 `urlpatterns` 배열에 넣어줘야 등록된다. 이부분도 다른 프레임웍이랑 다른 부분이다, 내부에서의 작동원리를 나중에 살펴봐야할듯..

앱의 라우트 파일은 글로벌 라우트 파일에 include해야 한다.

글로벌 라우트 파일인 `ex_django/urls.py`를 아래와 같이 수정한다.

```
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('polls/', include('polls.urls')),
    path('admin/', admin.site.urls),
]
```

`path`함수의 시그니처는 다른 프레임웍과 비슷하다.

```
def _path(route, view, kwargs=None, name=None, Pattern=None):
```

`include`함수는 위와 같이 route를 여러 파일에 분리하여 작성할 때 사용하는 함수이다. 예상대로 상위 라우트의 url prefix가 상속되어진다.


### 확인하기

브라우저에서 http://localhost:8000/polls/를 입력한다. index 컨트롤러에 정의한 "Hello, world. You're at the polls index." 가 보인다.