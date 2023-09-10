### Задание 1

**Что нужно сделать:**

1. Установите себе jenkins по инструкции из лекции или любым другим способом из официальной документации. Использовать Docker в этом задании нежелательно.
2. Установите на машину с jenkins [golang](https://golang.org/doc/install).
3. Используя свой аккаунт на GitHub, сделайте себе форк [репозитория](https://github.com/netology-code/sdvps-materials.git). В этом же репозитории находится [дополнительный материал для выполнения ДЗ](https://github.com/netology-code/sdvps-materials/blob/main/CICD/8.2-hw.md).
3. Создайте в jenkins Freestyle Project, подключите получившийся репозиторий к нему и произведите запуск тестов и сборку проекта ```go test .``` и  ```docker build .```.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

---
![image](https://github.com/Dk054/studies/assets/139000762/9628804a-a27d-438a-b773-2630f7b2dcd9)
![image](https://github.com/Dk054/studies/assets/139000762/6b713a89-137f-45c0-ad98-2ac61897c405)
![image](https://github.com/Dk054/studies/assets/139000762/5ea25644-5b44-41af-a065-65b860f50d6f)
![image](https://github.com/Dk054/studies/assets/139000762/28200b75-fe63-4f27-af5f-aee7f5fe4fac)


### Задание 2

**Что нужно сделать:**

1. Создайте новый проект pipeline.
2. Перепишите сборку из задания 1 на declarative в виде кода.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

---
''
pipeline {
 agent any
 options {
     skipDefaultCheckout true
}
environment {
    GO_DIR = '/usr/bin/'
}
stages {
stage('clone repo') {
 steps {
     git branch: 'main', url: 'https://github.com/Dk054/sdvps-materials.git', credentialsId: 'github_creds'}
  }
  stage('Test go') {
   steps {
    sh '${GO_DIR}go test .'
   }
  }
  stage('Docker build') {
   steps {
    sh 'docker build . -t ubuntu-bionic:8082/hello-world:v$BUILD_NUMBER'
   }
  }
  }
 }
 ''
![image](https://github.com/Dk054/studies/assets/139000762/948aa096-03c6-4759-bf2a-2e4516c64451)

### Задание 3

**Что нужно сделать:**

1. Установите на машину Nexus.
1. Создайте raw-hosted репозиторий.
1. Измените pipeline так, чтобы вместо Docker-образа собирался бинарный go-файл. Команду можно скопировать из Dockerfile.
1. Загрузите файл в репозиторий с помощью jenkins.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

---
## Дополнительные задания* (со звёздочкой)

Их выполнение необязательное и не влияет на получение зачёта по домашнему заданию. Можете их решить, если хотите лучше разобраться в материале.

---

### Задание 4*

Придумайте способ версионировать приложение, чтобы каждый следующий запуск сборки присваивал имени файла новую версию. Таким образом, в репозитории Nexus будет храниться история релизов.

Подсказка: используйте переменную BUILD_NUMBER.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.
