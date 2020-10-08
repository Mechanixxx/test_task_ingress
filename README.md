# test_task_ingress
**- Создаем два конфиг-файла (wello-world-1 и 2)**

**- Создаем конфиг Ingress**

**Для установки контроллера Ingress использовал Helm:**

*helm install hello-world nginx-stable/nginx-ingress*

**- Создаем pods:**

*kubectl create -f hello-world-1.yml*

*kubectl create -f hello-world-2.yml*

*kubectl create -f hello-world-ingress.yml*

**Задача выставить Ingress в сеть пока не решена :(**
