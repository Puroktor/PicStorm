# PicStorm
Android-приложение для просмотра и публикации фотографий. Предоставляет возможность фильрации публикаций, их оценки, поиска и подписки на других пользователей. Присутсвует возможность назначать админинстарторов, которые могут блокировать публиации и пользователей.<br>
* [Серверная часть](https://github.com/Puroktor/PicStorm-Backend)
* [Клиентская часть](https://github.com/Yokunnn/PicStorm-Frontend)

### Команда ТП-6.1-2
* [Кирилл Скофенко](https://vk.com/goosepusher) - тимлид, разработка backend
* [Егор Закаблуков](https://vk.com/crinzhulka) - разработка frontend
* [Евгений Баркалов](https://vk.com/eubarkalov) - документация

Подбробный отчет по ролям можно найти [здесь](https://github.com/Puroktor/PicStorm/blob/main/docs/Role_report.pdf)

### Краткое опсиание архитектуры проекта
Сервер написан на языке программирования Java с помощью фреймворка Spring Boot. Он сотоит из 3-х основных слоев:
* Контроллеров, обрабатывающих входящие запросы клиента
* Сервисов, реализующих бизнес-логику, также к этому слою относятся репозитории - интерфейсы для взаимодействия с базой данных, предоставляемые фреймворком
* Моделей, описывающих сущности, используемые в приложении
<a/>
Сервер использует принцип инверсии управления, при котором поток управления программы контролируется фреймворком. Реализуется он с помощью механизма внедрения зависимостей (DI). Такой подход позволяет уменьшить связность кода и  упростить расширение функционала и придерживаться принципа единой ответственности.
Взаимодействие с клиентом происходит в соответствии с REST архитектурой, без сохранения состояния между запросами. Для авторизации пользователей используются JWT токены. Документация API приложена ниже. Загружаемые пользователями фотографии хранятся в сервисе Yandex Object Storage, что позволяет легко масштабировать приложение. <br/>
Сервер поддерживает Docker Compose, поэтому для его запуска локально, достаточно в папке с исходным кодом проекта выполнить команду: <br><br>

```
docker compose up
```
<br>
Клиент написан на языке программирования Kotlin с использованием Android SDK. Он построен по архитектуре MVVM, также состоящей из 3-х слоев: <br><br>

* Моделей, описывающих сущности приложения. В нашем случае они разделены на зависимые от API сервера - пакет `data.*` и независимые - пакет `domain.*` 
* Представлений, отвечающий за представление данных
* Моделей представлений, реализующих взаимодействие отображений с сущностями, используемыми в приложении
<a/>

Клиент использует Single Activity подход. Переход между его фрагментами, осуществляется с помощью Navigation Component, в соотвествии с навигационным графом. <br>
Установочный файл приложения присутствует в репозитории.

### Использованные сервисы
* [Trello](https://trello.com/b/wCmoJOe9/picstorm-board) - таск-менеджер <br/>
**Note:** Для корректного отображения подзадач желательно (но необязательно) установить плагин SubTasks.<br/>Установка доступна после входа в аккаунт.

* [Miro](https://miro.com/app/board/uXjVMe7SI7o=/) - описание основных сценариев
* [Figma](https://www.figma.com/file/gzrFreOIXap1I7hpizGJG6/PicStorm) - интерактивный прототип
* [Swagger](http://158.160.39.62/swagger-ui/index.html) - документация API

### Документация
* [Техническое задание](https://github.com/Puroktor/PicStorm/tree/main/docs/Technical_Specification.pdf)
* [Курсовой проект](https://github.com/Puroktor/PicStorm/tree/main/docs/Course_Project.pdf)
* [Презентация](https://github.com/Puroktor/PicStorm/blob/main/docs/PicStorm_Slides.pdf)
### Видео
* [Обзор серверной части](https://youtu.be/tic_7vvU-pM)
* [Деплой сервера](https://www.youtube.com/watch?v=axCPy-4EUIQ)
### Данные главного администратора
В приложении PicStorm всегда присутсвует главный администратор. <br>
Его имя пользователя: `Главный Администратор` <br>
Пароль: `super-admin`
