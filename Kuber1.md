Задание 1
Выполните действия:

Запустите Kubernetes локально, используя k3s или minikube на свой выбор.
Добейтесь стабильной работы всех системных контейнеров.
В качестве ответа пришлите скриншот результата выполнения команды kubectl get po -n kube-system.

![1](https://user-images.githubusercontent.com/122460278/213149648-6db9b09f-c728-4f06-8db1-a97767a4fdc0.png)

![2](https://user-images.githubusercontent.com/122460278/213149657-5cea02fa-b26a-4f5a-b46d-2d60b02f9867.png)


Задание 2
Есть файл с деплоем:

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis
spec:
  selector:
    matchLabels:
      app: redis
  replicas: 1
  template:
    metadata:
      labels:
        app: redis
    spec:
      containers:
      - name: master
        image: bitnami/redis
        env:
         - name: REDIS_PASSWORD
           value: password123
        ports:
        - containerPort: 6379
Выполните действия:

Измените файл с учётом условий:
redis должен запускаться без пароля;
создайте Service, который будет направлять трафик на этот Deployment;
версия образа redis должна быть зафиксирована на 6.0.13.
Запустите Deployment в своём кластере и добейтесь его стабильной работы.
В качестве решения пришлите получившийся файл.

![3](https://user-images.githubusercontent.com/122460278/213149705-1766e3cb-29c9-4f70-8e8f-62eef01ca20c.png)


Задание 3
Выполните действия:

Напишите команды kubectl для контейнера из предыдущего задания:
выполнения команды ps aux внутри контейнера;
просмотра логов контейнера за последние 5 минут;
удаления контейнера;
проброса порта локальной машины в контейнер для отладки.
В качестве решения пришлите получившиеся команды.
![5](https://user-images.githubusercontent.com/122460278/213149994-1ddb6b14-6de1-45f2-a6a6-1fde2d27a7f3.png)




Дополнительные задания* (со звёздочкой)
Их выполнение необязательное и не влияет на получение зачёта по домашнему заданию. Можете их решить, если хотите лучше разобраться в материале.

Задание 4*
Есть конфигурация nginx:

location / {
    add_header Content-Type text/plain;
    return 200 'Hello from k8s';
}
Выполните действия:

Напишите yaml-файлы для развёртки nginx, в которых будут присутствовать:
ConfigMap с конфигом nginx;
Deployment, который бы подключал этот configmap;
Ingress, который будет направлять запросы по префиксу /test на наш сервис.
В качестве решения пришлите получившийся файл.
