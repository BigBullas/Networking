# Сетевые технологии

#### Образ виртуальной машины Linux [Ubuntu 20.04](https://github.com/iu5git/Standards/blob/main/Linux/Linux.md) для выполнения заданий курса


# Курсовой проект

### Сроки
- 3 неделя: Выбрать тему-вариант, определить команду и сформировать черновое ТЗ
- 8 неделя: чистовое ТЗ (исправление с учетом замечаний), макет figma, диаграмма прецедентов, ER-диаграмма, диаграмма развертывания, swagger

Чистовое ТЗ должно содержать требования к типу авторизации (сессии или JWT), описание ролей и функций пользователей

- 12 неделя: полный комплект документов (ТЗ, РПЗ, ПМИ, РП, РСА, диаграмма прецедентов, диаграмма последовательности, ER-диаграмма, диаграмма деятельности, диаграмма развертывания)
- 14-15 неделя: защита, презентация по диаграммам, демонстрация приложения, ответы на вопросы 

### Документация
1. Backend. ER, deployment. По характерному алгоритму нужно сделать activity и sequence diagram со стороны backend. Sequence diagram (отправка сообщения) - временная, соответственно timeline, основные компоненты backend, участвующие во взаимодействии и инициация взаимодействия от frontend
2. Frontend: Use Case. По характерному алгоритму нужно сделать activity и sequence diagram со стороны frontend. Sequence diagram (отправка сообщения) - временная, соответственно timeline, основные компоненты frontend, участвующие во взаимодействии и web-сервис backend
3. Сетевая (интеграционная) задача. По характерному алгоритму нужно activity и sequence diagram: SSO, микросервисы взаимодействия и S3
4. Руководство пользователя - фронтендер (более детально описание интерфейса и руководство по работе с приложением), руководство администратора - бекендер (системные требования, инструкция по развертыванию системы, для каких компонентов что потребуется). 
5. РПЗ - состоит из 2-3 частей, которые соответствуют каждому студенту: frontend (функции системы, ссылаетесь на use-case, описание пользовательского интерфейса по скриншоту, описание основного алгоритма взаимодействия по sequence, activity), backend (архитектура deployment, ER для описания базы данных и основные алгоритмы по sequence и activity), сетевая задача (архитектура deployment, основные алгоритмы по sequence и activity).
6. ПМИ (frontend, тот функционал, который он не может тестировать - бекендер и сетевик) - тестирование всего основного функционала приложения по пунктам заголовок, краткое описание с результатами и скриншот: отправка сообщения, авторизация, предоставление прав администратором пользователям, передача файла (у кого есть) и тд. При этом для сетевого функционала нужно привести результаты wireshark (то есть при обмене frontend-banckend bankend-network должны быть результаты с пакетами) компактно только характерные пакеты

[Примеры документации](/docs)

#### Проверка документации
1. Аналог Контроль ВКР
2. Проверка на плагиат

### Демонстрация
1. На защите презентация по шаблону. Диаграммы должны читаться на презентации, должны быть видны на экране ноутбука. Начать с цели, сути приложения. Потом прецеденты - пользователи, функции системы.
2. Далее по deployment - какие компоненты, кто реализовал, какие сетевые протоколы между вашими узлами есть. 
3. Потом каждый отвечает по своей части. Упор на сетевое взаимодействие: кто какие ноды/компоненты делал, какие протоколы 
4. В демонстрации указать или вкладку Network, или wireshark (особенно для тех, где есть сетевая задача) - сделать филтрацию по IP и протоколу для этого

#### 3 участника команды
1. **Фронтенд и аналитика**: 

- Документация: РП (руководство пользователя), часть РПЗ. Диаграммы прецедентов, диаграмма последовательности запросов и действий.
- Необходимо реализовать приложение на React + Redux Toolkit + Axios + MUI. Необходимо реализовать окно регистрации и авторизации. Приложение должно общаться с веб-сервису с данными, а при отсутствии подключения - отображать Mock-объекты (отобразить надпись, что нет подключения или вернуть закешированную страницу. Используйте Service Worker)

- [Инструкция по Figma MUI](https://github.com/iu5git/Standards/blob/main/docs/Tutorial_MUI.pdf)
- [Пример реализации приложения React](https://github.com/iu5git/web-2022/blob/main/tutorials/lab4/lab4_tutorial.md)
- [Пример использования Redux](https://github.com/iu5git/web-2022/blob/main/tutorials/redux/redux_toolkit.md)

2. **Бэкенд + QA**: 
 
- Документация: ПМИ (в приложении результаты тестирования), часть РПЗ. ER-диаграмма, диаграмма деятельности
- Необходимо реализовать веб-сервис (API gateway), который будет предоставлять методы для фронтенда. Веб-сервис взаимодействует с базой данных. Необходимо ограничить доступ к методам сервиса через авторизацию

- [Пример реализации веб-сервиса DRF](https://github.com/iu5git/web-2022/blob/main/tutorials/lab7-py/lab7_tutorial.md)
- [Пример реализации веб-сервиса Golang](https://github.com/iu5git/web-2022/blob/main/tutorials/lab7-go/README.md)

3. **Интеграция**: 
 
- Документация: РСА (руководство системного администратора), часть РПЗ. Диаграмма развертывания, диаграмма последовательности запросов или деятельности.
- Необходимо реализовать отдельный сервис, который реализует одну из перечисленных задач (см. ниже). Взаимодействие сервиса и бэкенда происходит по протоколу gRPC

- [Пример реализации микросервиса на GoLang и gRPC](https://habr.com/ru/post/461279/)

### Интеграционные задачи
1. **WebSocket**. Реализация собственного протокола прикладного уровня для передачи по WebSocket (сообщения/уведомления/статусы). Сервис ws взаимодействует с бэкендом по gRPC для получения/изменения данных. Гарантированная доставка сообщений при повторном подключении после разрыва соединения.

- [Пример взаимодействия через WebSocket](/Websocket)

2. **Брокер**. Микросервисы уведомлений: почта, telegram, vk. Бизнес-логика приоритетной отправки разных событий. Взаимодействие с бекендом-источником через gRPC. Гарантированная отправка через очередь сообщений с повторной отправкой при не достижении одного из клиентов. Случайная отмена/ошибка отправки. При возникновении ошибки при отправке источник получает информацию об этом. 

- [Пример установки Kafka через wsl](/kafka_wsl)

3. **S3-хранилище**. Синхронизация нескольких клиентов разных пользователей в облаке. Файлы, видео, музыка, заметки, фото. Локальные папки, облачные, совместные.

- [Пример подключения S3-хранилища](/S3)

4. **Блокчейн**.

5. **Кеширование**. Реализация сервиса с помощью резидентной БД Redis для кеширования данных  

#### Варианты
1. Интернет-магазин с уведомлениями
- Фронтенд: создание React-приложения магазина 
- Бэкенд: реализация веб-сервиса с БД для хранения товаров и покупок
- Брокер: реализация сервиса-брокера с помощью Kafka для гарантированной отправки уведомлений клиенту в приложение, а если он не в сети - в VK

2. Облачный календарь с синхронизацией и уведомлениями 
- Фронтенд: создание React-приложения календаря. Возможность работы offline
- Бэкенд: реализация веб-сервиса календаря с БД для хранения событий календаря, синхронизация новых данных с клиентом
- Брокер: реализация сервиса-брокера с помощью Kafka для гарантированной отправки напоминаний пользователю на почту

3. Облачные заметки с синхронизацией
- Фронтенд: создание React-приложения заметок. Возможность работы offline
- Бэкенд: реализация веб-сервиса с БД для создания, редактирования, удаления заметок. Синхронизация новых данных с клиентом
- S3-хранилище: реализация сервиса для хранения вложений заметок в S3

4. Облачные напоминания с синхронизацией и уведомлениями
- Фронтенд: создание React-приложения напоминаний. Возможность работы offline
- Бэкенд: реализация веб-сервиса с БД для создания, редактирования, удаления напоминаний. Синхронизация новых данных с клиентом
- Брокер: реализация сервиса-брокера с помощью Kafka для гарантированной отправки напоминаний пользователю на почту

5. Банк с уведомлениями
- Фронтенд: создание React-приложения счетов и операций банка
- Бэкенд: реализация веб-сервиса с БД для добавления карт/счетов/договоров и хранения платежей
- Брокер: реализация сервиса-брокера с помощью Kafka для гарантированной отправки уведомлений клиенту в приложение, а если он не в сети - на почту

6. Совместное редактирование документов
- Фронтенд: создание React-приложения просмотра и редактирования документов (аналог Google docs)
- Бэкенд: реализация веб-сервиса с БД для добавления, редактирования, просмотра, удаления текстовых документов
- WebSocket: реализация отдельного сервиса и модуля фронтенда для взаимодействия по WebSocket для редактирования документов

7. Система автоматической калибровки
- Фронтенд: создание React-приложения отображения данных измерений
- Бэкенд: реализация веб-сервиса с БД для сбора и сохранения данных измерений с криостата
- Кеширование: развертывание приложения, БД, настройка и развертывание Redis

8. Облачный компилятор через очередь
- Фронтенд: создание React-приложения редактирования скриптов Python
- Бэкенд: реализация веб-сервиса с БД для хранения скриптов, попыток выполнения и результатов
- Брокер: реализация сервиса-брокера с помощью Kafka для выполнения скриптов Python

9. Умный дом через веб-сокет
- Фронтенд: создание React-приложения для устройств умного дома и панели управления
- Бэкенд: реализация веб-сервиса с БД для хранения настроек устройств умного дома с привязкой к комнатам
- WebSocket: реализация отдельного сервиса и модуля фронтенда для передачи по WebSocket для взаимодействия устройств умного дома и панели управления

10. Сервис рецензирования конференции с уведомлениями
- Фронтенд: создание React-приложения для рецензирования публикаций конференции
- Бэкенд: реализация веб-сервиса с БД для хранения рецензий и публикаций
- Брокер: реализация сервиса-брокера с помощью Kafka для гарантированной отправки уведомлений автору в приложение, а если он не в сети - на почту

11. Система для передачи данных дистанционного зондирования
- Фронтенд: создание React-приложения для передачи данных зондирования Земли
- Бэкенд: реализация веб-сервиса с БД для хранения спутников-пользователей и метаданных о зондировании
- WebSocket: реализация отдельного сервиса и модуля фронтенда для гарантированной пакетной передачи по WebSocket данных-файлов зондирования

12. Чат с реакциями и ответами пользователей
- Фронтенд: создание React-приложения мессенджера с реакциями и ответами пользователей
- Бэкенд: реализация веб-сервиса с БД для хранения чатов и сообщений
- WebSocket: создание отдельного сервиса и модуля фронтенда для реализации протокола передачи по WebSocket сообщений и реакций 

13. Сайт поиска собеседников с чатом
- Фронтенд: создание React-приложения для поиска собеседников и диалогов
- Бэкенд: реализация веб-сервиса с БД для хранения данных о пользователе, диалогов и сообщений, реализация создания пар-диалогов 
- WebSocket: создание отдельного сервиса и модуля фронтенда для реализации протокола передачи по WebSocket сообщений и уведомлений о подборе пары-диалога

14. Сайт объявлений с чатом
- Фронтенд: создание React-приложения сайта объявлений с чатом по ним (аналог Авито)
- Бэкенд: реализация веб-сервиса с БД для хранения данных об объявлениях и сообщений
- WebSocket: создание отдельного сервиса и модуля фронтенда для реализации протокола передачи по WebSocket сообщений и уведомлений о новых сообщениях

15. Социальная сеть
- Фронтенд: создание React-приложения для списка друзей и диалогов с друзьями
- Бэкенд: реализация веб-сервиса с БД для хранения данных о пользователе, диалогов и сообщений; поиск друзей по нескольким полям
- WebSocket: создание отдельного сервиса и модуля фронтенда для реализации протокола передачи по WebSocket сообщений

~~16. Сайт текстовых трансляций~~
~~- Фронтенд: интерфейс текстовой трансляции~~
~~- Бэкенд: реализация ведения трансляции через web-socket, реализация создания трансляции~~
~~- WebSocket: развертывание приложения, БД~~

17. Сайт тематических форумов
- Фронтенд: создание React-приложения тематических форумов с представлением сообщений с ответами в виде дерева
- Бэкенд: реализация веб-сервиса с БД для хранения данных о форуме, обсуждениях и сообщениях
- WebSocket: создание отдельного сервиса и модуля фронтенда для реализации протокола передачи по WebSocket сообщений форума

18. Приложение для биржевой торговли
- Фронтенд: создание React-приложения приложения для биржевой торговли с отображением котировок в виде графика или стакана
- Бэкенд: реализация веб-сервиса с БД для хранения данных о ценных бумагах, котировках и операциях
- WebSocket: создание отдельного сервиса и модуля фронтенда для реализации протокола передачи по WebSocket данных о котировках акций

19. Сервис микроблогов с функцией пересылки-репоста
- Фронтенд: создание React-приложения сервиса микроблогов с комментариями и возможностью пересылки чужого сообщения
- Бэкенд: реализация веб-сервиса с БД для хранения данных о блогах, сообщениях и комментариях
- WebSocket: создание отдельного сервиса и модуля фронтенда для реализации протокола передачи по WebSocket сообщений и репостов

~~20. Отслеживания состояния очереди. (Сколько сообщений, содержание каждого сообщения, кто потребитель, отправлено/не отправлено)~~
~~- Фронтенд: создание React-приложения состояния очереди~~
~~- Бэкенд: реализация отслеживания состояния очереди через web-socket~~
~~- Брокер: развертывание приложения, БД, настройка и развертывание инструмента для реализации очереди (Kafka и т.д.)~~

~~21. Отправка сообщений с задержкой/в определенное время.~~
~~- Фронтенд: создание React-приложения чата~~
~~- Бэкенд: реализация ведения чата с сообщениями с задержкой, реализация сохранения сообщений в очереди~~
~~- Брокер: развертывание приложения, БД, настройка и развертывание инструмента для реализации очереди (Kafka и т.д.)~~

22. Сервис асинхронных расчетов через очередь
- Фронтенд: создание React-приложения ввода данных и параметров расчета
- Бэкенд: реализация веб-сервиса с БД для хранения входных данных и результатов расчетов
- Брокер: реализация сервиса-брокера с помощью Kafka для выполнения расчетов (подсчет факториала, нахождения НОД и тд)

23. Новостной сервис с подписками в Телеграм
- Фронтенд: создание React-приложения новостного сервиса
- Бэкенд: реализация веб-сервиса с БД для хранения новостей, тематик и подписок
- Брокер: реализация сервиса-брокера с помощью Kafka для гарантированной отправки подписчискам новостей по выбранным тематикам

~~24. Использование Redis для аварийного восстановления системы (восстановление системы с промежуточного состояния)~~
~~- Фронтенд: создание React-приложения отслеживания состояния системы~~
~~- Бэкенд: реализация аварийного восстановления системы, сохранение промежуточного состояния системы в Redis~~
~~- Брокер: развертывание приложения, БД, настройка и развертывание Redis~~

25. Сервис заявок госуслуг
- Фронтенд: создание React-приложения создания и обработки заявок на услуги
- Бэкенд: реализация веб-сервиса с БД для хранения услуг и заявок на них
- WebSocket: создание отдельного сервиса и модуля фронтенда для реализации протокола передачи по WebSocket статусов заявок и уведомлений

~~26. Асинхронная загрузка страницы с помощью кеша на Redis~~
~~- Фронтенд: интерфейс страницы на выбор~~
~~- Бэкенд: реализация передачи кешированных данных, сохранение промежуточных данных в Redis~~
~~- Брокер: развертывание приложения, БД, настройка и развертывание Redis~~

27. Облачное хранилище файлов конференции
- Фронтенд: создание React-приложения для подачи документов на конференцию (статья, разрешение на публикацию)
- Бэкенд: реализация веб-сервиса с БД для хранения данных об авторах и публикациях
- S3-хранилище: реализация сервиса для хранения документов в S3

28. Фотосервис
- Фронтенд: создание React-приложения фотосервиса
- Бэкенд: реализация веб-сервиса с БД для хранения альбомов пользователей
- S3-хранилище: реализация сервиса для хранения изображений в S3, пакетная загрузка нескольких изображений

29. Музыкальный сервис
- Фронтенд: создание React-приложения хранилища музыки
- Бэкенд: реализация веб-сервиса с БД для хранения плейлистов с музыкой
- S3-хранилище: реализация сервиса для хранения музыки в S3, пакетная загрузка нескольких треков

30. Видеохостинг
- Фронтенд: создание React-приложения видеохостинга
- Бэкенд: реализация веб-сервиса с БД для хранения каналов и метаинформации роликов
- S3-хранилище: реализация сервиса для хранения видео в S3

31. Синхронизация локального хранилища и S3
- Фронтенд: создание React-приложения хранения файлов в локальном хранилище с функцией передачи в удаленное хранилище
- Бэкенд: реализация веб-сервиса с БД для хранения данных 
- S3-хранилище: реализация сервиса для хранения документов в S3 с синхронизацией данных с клиента

~~32. Интеграция с S3. Загрузка частичных изменений текстовых файлов в облачное хранилище~~
~~- Фронтенд: интерфейс удаленного хранилища~~
~~- Бэкенд: реализация создания, редактирования, удаления музыки с синхронизацией с загрузкой частичных изменений текстовых файлов в облачное хранилище~~
~~- S3-хранилище: развертывание приложения, БД, настройка и развертывание S3~~

33. Система версионирования файлов
- Фронтенд: создание React-приложения удаленного файлового хранилища с возможностью версионирования
- Бэкенд: реализация веб-сервиса с БД для получения истории версии файлов и папок 
- S3-хранилище: реализация сервиса для хранения документов в S3 с добавлением и получением конкретной версии файла

~~34. Интеграция с S3. Уведомления об обновление файлов на сервере/локально при заходе в систему~~
~~- Фронтенд: интерфейс удаленного хранилища~~
~~- Бэкенд: реализация создания, редактирования, удаления музыки с синхронизацией с уведомлениями об обновление файлов на сервере/локально при заходе в систему~~
~~- S3-хранилище: развертывание приложения, БД, настройка и развертывание S3~~

~~35. Интеграция с S3. Возможность постановки на паузу и одновременная загрузка нескольких файлов~~
~~- Фронтенд: интерфейс удаленного хранилища~~
~~- Бэкенд: реализация создания, редактирования, удаления музыки с синхронизацией с возможностью постановки на паузу и одновременная загрузка нескольких файлов~~
~~- S3-хранилище: развертывание приложения, БД, настройка и развертывание S3~~

~~36. Отмена отправки сообщений через очередь (те, кто успел получить - получили, те, кто не успел - не должны получить)~~
~~- Фронтенд: интерфейс создания сообщений в чате~~
~~- Бэкенд: реализация создания и обработки сообщений с помощью очереди с отменой отправки~~
~~- Брокер: развертывание приложения, БД, настройка и развертывание инструмента для реализации очереди (Kafka и т.д.)~~

~~37. Морской бой Онлайн~~
~~- Фронтенд: интерфейс игры~~
~~- Бэкенд: реализация комнат, передачи данных противника по web-socket, сохранение статистики в БД~~
~~- WebSocket: развертывание приложения, БД~~

38. Шахматы Онлайн
- Фронтенд: React приложение для игры, отображение фигур, счета. Проверка допустимых ходов и очередности игроков
- Бэкенд: реализация веб-сервиса с БД для хранения статистики, результатов игр и ходов игроков. Подбор свободных игроков для игры
- WebSocket: создание отдельного сервиса и модуля фронтенда для реализации протокола передачи по WebSocket ходов игроков, блокировка игроков по очередности

39. Шашки Онлайн
- Фронтенд: React приложение для игры, отображение фишек, счета. Проверка допустимых ходов и очередности игроков
- Бэкенд: реализация веб-сервиса с БД для хранения статистики, результатов игр и ходов игроков. Подбор свободных игроков для игры
- WebSocket: создание отдельного сервиса и модуля фронтенда для реализации протокола передачи по WebSocket ходов игроков, блокировка игроков по очередности

~~40. Сайт-аукцион (ebay)~~
~~- Фронтенд: интерфейс сайта-аукциона~~
~~- Бэкенд: реализация обновление списка товаров и актуальных ставок через web-socket~~
~~- WebSocket: развертывание приложения, БД~~

~~41. Лента новостей с реакциями~~
~~- Фронтенд: интерфейс ленты новостей~~
~~- Бэкенд: реализация добавления новых новостей, возможность оставлять реакции и получать push-уведомления, если кто-то оставил реакцию на вашу новость, через web-socket~~
~~- WebSocket: развертывание приложения, БД~~

~~42. Домино Онлайн~~
~~- Фронтенд: интерфейс игры~~
~~- Бэкенд: реализация комнат, передачи данных противника по web-socket, сохранение статистики в БД~~
~~- WebSocket: развертывание приложения, БД~~

43. Хостинг html-страниц и отображение на странице
- Фронтенд: React приложение для хостинга пользовательских html-страниц, страница отображения страниц
- Бэкенд: реализация веб-сервиса с БД для хранения данных о микросайтах пользователей
- S3-хранилище: реализация сервиса для хранения html-страниц в S3

44. Blockchain-сервис документооборота в медицинской сфере
- Фронтенд: создание React-приложения для хранения медицинских данных
- Бэкенд: реализация веб-сервиса с БД для хранения данных о пользователях
- Блокчейн: создание сервиса для взаимодействия с хранилищем blockchain

45. Совместные заметки
- Фронтенд: создание React-приложения заметок
- Бэкенд: реализация веб-сервиса с БД для хранения заметок
- WebSocket: создание отдельного сервиса и модуля фронтенда для реализации протокола синхронизации через long polling заметок

#### Запасные варианты
Морской бой Онлайн
- Фронтенд: интерфейс игры
- Бэкенд: реализация комнат, передачи данных противника по web-socket, сохранение статистики в БД
- WebSocket: развертывание приложения, БД

Сайт-аукцион (ebay)
- Фронтенд: интерфейс сайта-аукциона
- Бэкенд: реализация обновление списка товаров и актуальных ставок через web-socket
- WebSocket: развертывание приложения, БД

Лента новостей с реакциями
- Фронтенд: интерфейс ленты новостей
- Бэкенд: реализация добавления новых новостей, возможность оставлять реакции и получать push-уведомления, если кто-то оставил реакцию на вашу новость, через web-socket
- WebSocket: развертывание приложения, БД

Домино Онлайн
- Фронтенд: интерфейс игры
- Бэкенд: реализация комнат, передачи данных противника по web-socket, сохранение статистики в БД
- WebSocket: развертывание приложения, БД

# Сети и Телекоммуникации

Первое ДЗ - диаграмма развёртывания для архитектуры и диаграмма последовательности для описания сетевого алгоритма.

Второе ДЗ - реализация программы. 

### Варианты ДЗ:
#### 1. Обмен статусами собеседников через WebSocket 
Необходимо реализовать механизм обмена сообщениями между двумя собеседниками по протоколу WebSocket. Должна быть предусмотрена гарантированная отправка: если сообщение было отправлено на сервер, оно должно быть доставлено получателю при его подключении.

Синхронизация версий: если какое-то сообщение пришло раньше-позже (вследствие задержек), то есть отображать нужно версии в порядке отправки. 

- Требования к приложению:
1. В системе должен быть сервер приложения и два клиента.
2. У клиентов должна быть возможность подключиться/отключиться с определенным идентификатором и отправить сообщение
3. Обмен по WebSocket и HTTP
4. Если установлено соединение с двумя клиентами с одним идентификатором, то сообщение должно появляться у обоих.

- Порядок показа:
1. При показе нужно установить соединение двух клиентов с сервером
2. В браузере нужно показать запрос на изменение протокола
2. Отправить сообщение по-очереди с двух клиентов
3. Отключить второй клиент и отправить после этого сообщения с первого
4. Подключить второй клиент - должна отобразиться корректная история сообщений. На сервере в логах нужно увидеть отправленные сообщения

[Пример взаимодействия через WebSocket](/Websocket)

#### 2. Отправка email, телеграм, vk через очередь сообщений
Необходимо разработать два сервиса для отправки сообщений: брокер с очередью сообщений и сервис отправки. У каждого студента один из источников (email, телеграм, vk) по варианту. За счет очереди должна быть предусмотрена гарантированная отправка в случае недоставки сообщения. Если сообщение не было доставлено, оно повторно отправляется из очереди.  

- Требования к приложению:
1. Брокер
2. Демонстрация с помощью клиентов почты/телеграм/vk

- Порядок показа:
1. При включенном подключении к интернету отправить сообщение в брокер. Сообщение должно быть отправлено один раз получателю
2. Отключить от интернета. В шлюзе сообщений должна быть видна история попыток отправить уведомление. После последней попытки должно быть выведено сообщение об ошибке/ручной обработке

Можно использовать `Redis`, `Apache Kafka`, `RabbitMQ`

[Пример установки Kafka через wsl](/kafka_wsl)

#### 3. Отправка, получение файлов в файловом хранилище 
Необходимо настроить файловое хранилище S3 и разработать методы доступа к нему. Хранилище необходимо для синхронизации двух узлов (условные клиент и сервер облака). Должна быть предусмотрена синхронизация, если одна из версий устарела (на клиенте не было интернета)

- Требования к приложению:
1. Клиент и сервер. На клиенте есть возможность загружать файлы и из отправлять
2. Обмен по HTTP

- Порядок показа:
1. Загрузить новый файл на клиент, отправить на сервер. Файл должен загрузиться на сервер
2. Обновить файл на сервере (напрямую или через второй клиент)
3. Попытаться отправить файл на клиенте повторно. Обновление на сервере не должно произойти, на клиент должна вернуться версия файла с сервера.

Рекомендуется использовать `ceph`

[Пример подключения S3](/S3)

#### 4. Сервис блокчейна
Необходимо реализовать функционал добавления клиентской информации (документа) в цепочку блоков, их подписью, и централизованным/децентрализованным хранением.

Рекомендуется использовать `ethereum`

#### Команда курса выражает благодарность за помощь в подготовке материалов для данного курса
1. Коновалов Максим Владиславович
2. Балабанов Алексей Олегович
3. Торжков Максим Сергеевич
