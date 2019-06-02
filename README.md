# python django

download : https://www.python.org/downloads/

- django 는 웹 애플리케이션 프레임워크 (무료)
- 공식 사이트: http://www.djangoproject.com

python 설치 후 vscode python 및  python for vscode 설치

가상환경 만들기
- 다운로드 : https://pypi.org/project/pip/
- 설치 경로: cd \util\python\python37-32\Scripts
- pip install virtualenv
- virtualenv Project1
- cd \Project1\Scripts
- .\activate

활성화 종료: deactivate 

장고 설치 하기 

- pip 최신버전 업데이트 확인: python -m pip install --upgrade pip
- pip install Django==2.2.1


설치확인

- (Project1) PS E:\workspace\python\Project1\Scripts> .\python
- Python 3.7.3 (v3.7.3:ef4ec6ed12, Mar 25 2019, 21:26:53) [MSC v.1916 32 bit (Intel)] on win32
- Type "help", "copyright", "credits" or "license" for more information.
- >>> import django
- >>> print(django.get_version())
- 2.2.1

혹은 

- py -m django --version

장고 기본 디렉토리 설치
- 프로젝트 폴더, basic file templates, 그리고 프로젝트 관리 스크립트 (manage.py)를 만들기 위해서 django-admin 을 사용합니다.
- django-admin startproject mysite
- py manage.py runserver 

- py manage.py startapp catalog (이름은 아무거나 해도 상관은 없음) => 일단 만들어 놓고 다음시간에 작성

Admin 페이지 만들기
- 관리자 계정을 생성하기 위해서는 먼저, migrate
- createsuperuser :  admin 페이지에 로그인 하기 위한 정보들을 입력

- py manage.py migrate
- py manage.py createsuperuser
- unzena / 숫자(6개기억하기 42*****)

- 어플리케이션 실행 py manage.py runserver

catalog app 만들기
- py manage.py startapp blog
- setings.py에 blog app 작성 (어플리케이션 사용하겠다 등록 하는 작업)
- models.py 작성 
  -- (모델정의 https://docs.djangoproject.com/en/2.0/ref/models/fields/#field-types 참고)
- py manage.py makemigrations blog (장고에게 모델에 변경이 있었다는 것을 알려주는 것)
- py manage.py migrate blog (데이터베이스에 추가)
- blog/admin.py 작성

```
from django.contrib import admin
from .models import Post

admin.site.register(Post)
```

배포
- www.pythonanywhere.com
- clone => bash 선택 후 =>  git clone https://github.com/unzena/pythonTest.git
- tree pythonTest
- PythonAnywhere에서 가상환경(virtualenv) 생성하기
- cd pythonTest/
- virtualenv --python=python3.7 project1
- source project1/bin/activate
- pip install django~=2.2
- database 생성
- cd mysite
- .sqlite3 가 설정되었을 경우 먼저 삭제 후 migrate 
- python manage.py migrate
- python manage.py createsuperuser

web app으로 블로그 배포하기
- Web 대시보드 =>  Add a new web app => manual configuration => Python 3.7을 선택하고 다음(Next)을 클릭
- Virtualenv => /home/unzena/pythonTest/project1 저장

WSGI 파일 설정
- code 탭에 var/www/<your-username>_pythonanywhere_com_wsgi.py 부분 클릭
- 아래 소스 복사 후 붙여 넣기
```
import os
import sys

path = '/home/unzena/pythonTest/mysite'  # PythonAnywhere 계정으로 바꾸세요.
if path not in sys.path:
    sys.path.append(path)

os.environ['DJANGO_SETTINGS_MODULE'] = 'mysite.settings'

from django.core.wsgi import get_wsgi_application
from django.contrib.staticfiles.handlers import StaticFilesHandler
application = StaticFilesHandler(get_wsgi_application())
```
- 저장(Save)을 누르고 웹(Web) 탭
- reload 클릭 
- 배포 완료 unzena.pythonanywhere.com 