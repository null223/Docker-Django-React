Docker環境内でDjangoとReactを連携させて起動する初期設定例  

Django `localhost:8000/`  
React `localhost:3000/`  

TOPページは`localhost:3000/`  
※DjangoをWebAPIとして使う方法（react-routerなどが使えない可能性がある。）  

Makefileにてショートカットを登録してあります。  
xcodeのインストールを必要とされます。`xcode-select --install`　　


使用例：
```
make django
make app=todos
```
```
app:    docker-compose run --rm app sh -c "python manage.py startapp ${app}"

test:    docker-compose run --rm app sh -c "pytest -l -v -s ${app} && flake8"

migrate:
    docker-compose run --rm app sh -c "python manage.py makemigrations"
    docker-compose run --rm app sh -c "python manage.py migrate"

pro:    docker-compose run --rm app sh -c "django-admin startproject ${pro} ."

admin:    docker-compose run --rm app sh -c "python manage.py createsuperuser"

django:    docker-compose run --rm app sh -c "django-admin startproject app ."

react:    docker-compose run --rm react sh -c "create-react-app frontend"

```