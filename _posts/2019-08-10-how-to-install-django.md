---
title: "django 설치하기"
date: 2019-08-12 14:20:00 +0900
categories: python django
---
django를 배우는 첫번째 단계, 설치부터 해보자

# 준비

설치환경:
- OS: macOS Mojave 10.14.5
- python3: 3.7.3

현재 django의 가장 최신버전인 2.2버전을 python3에 설치할 예정이다.

> https://docs.djangoproject.com/ko/2.2/intro/install/


# django 설치

> 실제 django의 설치는 [이 문서](https://docs.djangoproject.com/ko/2.2/topics/install/#install-the-django-code)를 참고했다.

python3를 사용할 것이기 때문에 `pip` 대신 `pip3`를 사용하여 설치한다.

`pip3 install django`

```
khongchi@MAC:~/dev$ pip3 install django
Collecting django
  Downloading https://files.pythonhosted.org/packages/d6/57/66997ca6ef17d2d0f0ebcd860bc6778095ffee04077ca8985928175da358/Django-2.2.4-py3-none-any.whl (7.5MB)
    100% |████████████████████████████████| 7.5MB 682kB/s
Collecting sqlparse (from django)
  Downloading https://files.pythonhosted.org/packages/ef/53/900f7d2a54557c6a37886585a91336520e5539e3ae2423ff1102daf4f3a7/sqlparse-0.3.0-py2.py3-none-any.whl
Collecting pytz (from django)
  Downloading https://files.pythonhosted.org/packages/87/76/46d697698a143e05f77bec5a526bf4e56a0be61d63425b68f4ba553b51f2/pytz-2019.2-py2.py3-none-any.whl (508kB)
    100% |████████████████████████████████| 512kB 6.0MB/s
Installing collected packages: sqlparse, pytz, django
Successfully installed django-2.2.4 pytz-2019.2 sqlparse-0.3.0
```

# 설치확인 

제대로 설치되었는지 검토한다.

```
khongchi@MAC:~/dev$ python3
Python 3.7.3 (v3.7.3:ef4ec6ed12, Mar 25 2019, 16:52:21)
[Clang 6.0 (clang-600.0.57)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import django
>>> print(django.get_version())
2.2.4
>>>
```

# 프로젝트 생성

이제 프로젝트를 생성한다.

> https://docs.djangoproject.com/ko/2.2/intro/tutorial01/

`django-admin startproject ex_django`

```
khongchi@MAC:~/dev$ django-admin startproject ex_django
khongchi@MAC:~/dev$ cd ex_django/
khongchi@MAC:~/dev/ex_django$ tree
.
├── ex_django
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── manage.py
khongchi@MAC:~/dev/ex_django$
```

# 프로젝트 실행(서버 실행)
프로젝트가 생성되었으니 일단 한번 돌려보자. 아래 커맨드는 python에서 제공하는 경량 웹서버를 구동시킨다.

`python3 manage.py runserver`

```sh
khongchi@MAC:~/dev/ex_django$ python3 manage.py runserver
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).

You have 17 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.

August 10, 2019 - 08:08:00
Django version 2.2.4, using settings 'ex_django.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

브라우저에서 확인해보자

http://127.0.0.1:8000/ 에 접속한다.

로켓이 날라가는 화면이 나오면 성공!

