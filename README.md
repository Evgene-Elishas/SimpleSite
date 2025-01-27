# SimpleSite
Простенький сайт, на котором я обучаюсь веб-разработке

## На данный момент реализовано:
1. Простое пиксельное поле с возможностью приближения (колёсиком мыши изменяется размер: отдаление и приближение к точке на поле на которой курсор) и перемещения (движением мыши по полю при зажатой правой кнопке)
2. Движок для создания, запуска и остановки игр подобных игре "Жизнь" с различными видами соседства и наборами правил. Возможность добавления нескольких правил (выполняющихся поочерёдно), изменения порядка, временного отключения и редактирования.
3. Отрисовка игрового поля в пиксельное
4. Заполнение игрового поля с определённой частотой, его очистка
5. Возможность изменения состояния клетки на поле кликом, а также ведением при зажатой левой кнопке мыши (по сути рисование на поле)

## Запуск:
На данный момент используется 

*<script type="module" src="js/main.js"></script>* 

На который жалуются браузеры, если открывать сайт локально. Решение: запустить локальный сервер (временное решение)

*py -m http.server 8000 --directory \life*

Таким образом открывать сайт следует через **StartServer_OpenSite.bat**

## В будущем планируется:
### Основное:
* Проверить работу всего функционала на разных браузерах, уточнить начиная с каких версий работают все функции
* Сделать мобильную версию сайта + проверить работу на экранах разных размеров, чтобы всё отрабатывало корректно
* Проверить что изменение размеров поля и движение по нему адекватно отрабатывает на всех браузерах. Реализовать аналогичные функции на телефоне
* Поучиться работать с кэшем. Часть информации (состояние поля, активные правила) хранить в локальном хранилище, чтобы при обновлении страницы всё оставалось. Сделать возможность сброса всех параметров
* Сделать возможность сохранять поле как картинку файлом
* Доработать отрисовку клеток: добавить бортики.
* Добавить сверху полоску. Название, ссылка на гитхаб, описание что делать. В гитхабе сделать описание работы в виде гифки
### Исправления:
* Исправить проблему: если быстро двигать мышью, то рисование происходит не по всему пути, а отдельными точками через несколько клеток.  Вероятно это из-за того что  сигналы события движения мыши приходит недостаточно часто, и соответственно мышь оказывается не на соседних клетках. Доработать функцию, изменять состояние не только у текущей клетки, а на всём пути от предыдущей до текущей (подумать, как эффективно просчитать пересечение клеток) по прямой... Ну либо сделать что-то вроде кейлоггера, который будет отслеживать мышь точнее
* Починить баги в таймере, сделать проверку сколько реально времени занимает цикл. Решить проблему сотключением скрипта браузером (но чтоб он не нагружал систему)
* Исправить проблему: при быстрой чистоте смене кадров, отрисовка тормозит при рисовании и движении/изменения размеров поля. Добавить асинхронность (глянуть "javascript асинхронные функции")
### Более сложные доработки:
* Сделать динамически расширяющееся поле. Нужно чтобы при появлении активных клеток за пределами поля, оно расширялось под них, чтобы всё продолжило корректно работать. Возможно стоит реализовать поле не как двумерный массив, а как словарь (ключ — хеш-функция от координат) живых клеток и соседних (которые могут стать живыми на следующем шаге), и все проверки производить только с ними. Нужно придумать как оптимизировать производительность при этом. Продумать, когда делать остановку (в случае если клеток станет слишком много и они либо забьют память, либо каждый шаг алгоритма будет слишком долго работать)
* Расширить на полноценный сайт с несколькими вкладками. Главная страница с описанием и для переходов. Страница с игрой. Страница для рисования пиксельартом (докинуть палитру мб 256цветов). Сделать возможность портирования изображения между вкладками. Подумать о дальнейшем расширении
* Возможность регистрации, хранения и обработки инфы на сервере. Продумать проблемы безопасности (избегать доступа к чужим данным, изучить различные способы атак на сайты и противодействия им, и вообще как другие люди устраивают системы безопасности на сайтах), состояние гонки, и прочие вещи связанные с наличием более одного пользователя
* Расшарить на интернет, т.е. поднять хост
* Возможно переписать всё на нормальном фреймворке (Node.js, Angular, Vue.js, Redux, Bootstrap, JQuery, React, Three.js, какие там ещё есть...)
* Грамотнее разбить модули, чтобы они адекватнее взаимодействовали друг с другом, легко дорабатывались и не ломали друг друга. Продумать общую логику работы и АРХИТЕКТУРУ сайта. Избавиться от глобальных переменных по возможности. Возможно некоторые модули доработать так, чтобы их можно было использовать и на других (в будущем созданных) сайтов
### Ну и очевидные абстрактные мелочи:
* Подумать что можно убрать лишнего, и что ещё добавить
* Подумать над оптимизацией отрисовки.
* В целом оптимизировать производительность
* Отловить различные возможные ошибки
* Подумать что можно убрать лишнего, и что ещё добавить
* Просто в браузере глянуть "игра жизнь", как выглядит, как красиво отрисовать. как выглядят приложения для пиксельарта тоже глянуть
