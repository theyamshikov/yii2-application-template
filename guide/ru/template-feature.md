Особенности шаблона
===

За основу был взят шаблон [Yii 2.0 Advanced Application Template](https://github.com/yiisoft/yii2-app-advanced).

Нововведения:

* Точки входа `index.php` стали более чистыми и гибкими
* Конфигурация стала удобнее и проще
* [Структуру файлов конфигураций можно легко кастомизировать](https://github.com/yii2rails/yii2-app/blob/master/guide/ru/config.md)
* [Инициализация проекта стала более гибкой](https://github.com/yii2bundle/yii2-init/blob/master/guide/ru/init.md)
* [Вместо модели (**M**) используется парадигма *Domain-Driven Design* (**DDD**)](https://github.com/yii2rails/yii2-domain/blob/master/guide/ru/README.md)
* Разработан каркас админки
* Разработаны необходимые утилиты
* [Стандартизирован процесс сборки конфигов и запуска приложения](https://github.com/yii2rails/yii2-app/blob/master/guide/ru/README.md)
* Стандартизирован процесс разработки и тестирования **REST API**
* [Стандартизирован процесс создания сторонних компонентов (**composer**-пакетов)](https://github.com/yii2tool/yii2-vendor/blob/master/guide/ru/README.md)
* Стандартизирован процесс ведения документации
* Поддержка версионирования **доменных сущностей** и **REST API**
* [Поддержка мультиязычности](https://github.com/yii2bundle/yii2-lang/blob/master/guide/ru/README.md)
* [Гостевой режим](https://github.com/yii2guide/yii2-app/blob/master/guide/ru/guest-mode.md)
* Вся системная логика и часто используемая бизнес логика перенесена в зависимости
* Чистый шаблон приложения имеет примерно *90%* конфигов и данных, и *10%*  рабочего кода
* [Есть возможность прозрачно делить проект на микросервисы](https://github.com/yii2rails/yii2-domain/blob/master/guide/ru/multi-server-design.md)
* Работают "*из коробки*":
	* Пользователи
	* RBAC
	* Профиль
	* Мультиязычность
	* REST-клиент для работы с **API** приложением
	* Модуль руководства
	* Модуль статей
	* Стартовая страница
	* Система уведомлений (SMS, Email...)
	* Шифратор

Т. е. приложение изначально имеет часто используемый функционал.
При необходимости, лишнее можно отключить.

Шаблон включает в себя 4 приложения:

* API
* Пользовательская часть
* Админка
* Консоль

каждый из которых представляет собой отдельное приложение.

Доменный слой хранится в папке: `domain`.
Он не должен зависеть от приложений, модулей.
Доменный слой - это самостоятельный пучок компонентов.

API представляет собой агрегатное приложение, в ктором содержатся дочерние приложения.
Дочернее приложение API равно версии. 
Оно содержит свои конфиги, модули, тесты, документацию.
То есть, когда мы начинаем разработку новой версии API,
создаем дочернее приложение.
Например для второй версии API создаем приложение в папке `api/v2`.
Паралельно заводим доменный слой под версию API: `domain/v2`
Идея тут в том, чтобы делая новую версию функционала, не поломать старый функционал.
