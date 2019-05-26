# python django

download : https://www.python.org/downloads/

django 는 웹 애플리케이션 프레임워크 (무료)
공식 사이트: http://www.djangoproject.com

python 설치 후 vscode python 및  python for vscode 설치

가상환경 만들기
다운로드 : https://pypi.org/project/pip/
설치 경로: cd \util\python\python37-32\Scripts
pip install virtualenv
virtualenv Project1
cd \Project1\Scripts
activate Project1

활성화 종료: deactivate 

장고 설치 하기 

pip 최신버전 업데이트 확인: python -m pip install --upgrade pip
pip install Django==2.2.1


설치확인

(Project1) PS E:\workspace\python\Project1\Scripts> .\python
Python 3.7.3 (v3.7.3:ef4ec6ed12, Mar 25 2019, 21:26:53) [MSC v.1916 32 bit (Intel)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import django
>>> print(django.get_version())
2.2.1

혹은 

py -m django --version

장고 기본 디렉토리 설치
프로젝트 폴더, basic file templates, 그리고 프로젝트 관리 스크립트 (manage.py)를 만들기 위해서 django-admin 을 사용합니다.
django-admin startproject mysite
python3 manage.py runserver 


다음시간에...

py manage.py startapp catalog
