**Настройка простого Ingress-контроллера:**

*На выходе получаем 2 Pod-а (web и web2) - две версии сервиса.*

*Если запуск производился на локальной машине, сервис доступен из браузера по адресу http://hello-world.info или http://hello-world.info/v2*

***Порядок действий:***

**1. Включаем addon Ingress:**

	- minikube addons enable ingress
	
**2. Проверяем, что все работает:**

	- kubectl get pods -n kube-system
	
**3. Создаем развертывание и вешаем на порт:**

	- kubectl create deployment web --image=gcr.io/google-samples/hello-app:1.0
	
	- kubectl expose deployment web --type=NodePort --port=8080
	
**4. Проверяем, доступна ли служба:**

	- kubectl get service web
	
**5. Получаем адрес:**

	- minikube service web --url
	
**6. Копируем полученный вывод в браузер и стучимся на сервис. Вывод:**

	Hello, world!
	Version: 1.0.0
        Hostname: web-55b8c6998d-8k564
        
**7. Создаем файл Example-Ingress.yml**

**8. Создаем ресурс из него:**

	- kubectl apply -f example-ingress.yaml
	
**9. Проверяем, назначен ли IP адрес:**

	- kubectl get ingress
	
**10. Добавляем сопоставление адреса доменному имени в /etc/hosts**

**11. Проверяем:**

	- curl hello-world.info
	
	Вывод должен быть:
	
	Hello, world!
	Version: 1.0.0
        Hostname: web-55b8c6998d-8k564
        
**12. Для создания второго хоста повторить п3-5, где web заменяется на web2**



