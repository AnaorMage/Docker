# Отчет по лабораторной работе: Docker

## Задача 1 и 2: Сборка и публикация
Я собрал кастомный образ на базе `nginx:1.21.1` и отправил его в Docker Hub.
* **Ссылка на образ:** https://app.docker.com/accounts/anaor

Запуск и Push <img width="1920" height="832" alt="laba3" src="https://github.com/user-attachments/assets/37775930-dc5c-47a1-b6c3-881ad748e33f" />

Работа в браузере <img width="1917" height="639" alt="{EFC6381B-95A4-45D3-8F13-DB3F3D3ACD09}" src="https://github.com/user-attachments/assets/d896aeab-c9c1-4d81-985a-edaf057abbbb" />


---

## Задача 3: Эксперименты с конфигурацией
1. **Почему контейнер остановился после Ctrl+C?**
При использовании `attach` сигнал прерывания передается основному процессу (PID 1). Так как Nginx завершился, контейнер тоже остановился.

<img width="1414" height="207" alt="{26D37B27-C676-400F-802D-6AB5B7A3EF59}" src="https://github.com/user-attachments/assets/ea68f598-57ed-40e3-864e-8d1940972e26" />


2. **Проблема со сменой порта:**
После изменения порта с 80 на 81 внутри контейнера, внешний доступ через `localhost:8080` пропал.
**Суть проблемы:** Проброс портов (Mapping) статичен. Docker ждет трафик на 80 порту контейнера, а Nginx теперь слушает 81.

Ошибка curl <img width="1167" height="170" alt="{2770DF3C-BF7F-42B6-9330-B717F058B4AD}" src="https://github.com/user-attachments/assets/a94dca5f-bc85-412c-b244-8b2612629b9b" />


---

## Задача 4: Shared Volumes
Я запустил два контейнера (CentOS и Debian) с общей папкой. Файлы, созданные в одном, видны в другом.

Проверка Volumes <img width="1364" height="563" alt="4 (2)" src="https://github.com/user-attachments/assets/3415a80a-3807-4377-8c2c-9154aaaf1b8e" />


---

## Задача 5: Docker Compose и Portainer
С помощью Docker Compose была развернута инфраструктура, включающая кастомный сайт и панель управления Portainer.

Установка docker-compose <img width="1136" height="483" alt="5 1" src="https://github.com/user-attachments/assets/64e33e78-16d6-483d-aa77-25fa99ebd79c" />

Запуск и статус контейнеров <img width="1918" height="692" alt="5 2" src="https://github.com/user-attachments/assets/577b39c9-b2a2-4c42-b523-0c150c4cd152" />

Portainer <img width="1804" height="884" alt="{180FAC0F-21B2-4432-BB1A-DF0EC0E06D06}" src="https://github.com/user-attachments/assets/7cdc9604-ca5e-4051-9435-9ef5610bc75b" />

