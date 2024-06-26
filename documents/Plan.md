<h1 align="center">План автоматизации тестирования сценария покупки тура в Марракеш и заполнения формы покупки .</h1>
</br>

## 1. Перечень автоматизированных сценариев

#### Тестовые данные:

* Сервис обрабатывает только специальные номера карт, которые предоставлены для тестирования:

    * APPROVED карта - `1111 2222 3333 4444`
    * DECLINED карта - `5555 6666 7777 8888`

#### Сценарий навигации:

* Режим «Купить»
   
    * открыть веб-страницу турфирмы по адресу `http://localhost:8080/`
    * нажать кнопку `Купить`
    * появляется форма "Оплата по карте"
    * заполнить форму
    * нажать кнопку `Продолжить` 

* Режим «Купить в кредит»
   
    * открыть веб-страницу турфирмы по адресу `http://localhost:8080/`
    * нажать кнопку `Купить в кредит`
    * появляется форма "Кредит по данным карты"
    * заполнить форму
    * нажать кнопку `Продолжить`
 
#### Позитивные сценарии:

* После нажатия кнопки «купить» успешное появление формы «Оплата по карте»
    * Поле «Номер карты» состоит из 16 цифр для тестирования предоставлены специальные номера карт APPROVED и DECLINED.
    * Поле «Месяц» допустимое значение из двух цифр от 01 до 12.
    * Поле «Год» допустимое значение из двух последних цифр года.
    * Поле «Владелец» допустимое значение из двух комбинации латинских букв, разделённые пробелом (имя и фамилия пользователя), возможно наличие одного дефиса.
    * Поле «CVC/CVV» допустимое значение любая комбинация из трёх цифр. 
* После заполнения формы «Оплата по карте» валидными данными и нажатием кнопки «Продолжить» сообщение об успешной обработки платежа.

* После заполнения формы «Оплата по карте» номера карты со статусом "Declined" и нажатием кнопки «Продолжить» сообщение об отклонении платежа.

* После нажатия кнопки «купить в кредит» успешное появление формы «Кредит по данным карты».

* После заполнения формы «Кредит по данным карты» валидными данными и нажатием кнопки «Продолжить» сообщение об успешной обработки платежа.

* После заполнения  формы «Кредит по данным карты» номера карты со статусом "Declined" и нажатием кнопки «Продолжить» сообщение об отклонении платежа.

#### Негативный сценарий заполнения форм «Оплата по карте» и «Кредит по данным карты»

* Заполнение поля «Номер карты»
    
    * Ввод номера из 16 цифр отсутствующий в базе данных в поле номер карты .
    * Ввод номера карты менее 16 цифр.
    * Ввод спецсимволов в поле номер карты.
    * Ввод букв на кириллице в поле номер карты.
    * Ввод букв на латинице в поле номер карты.
    * Ввод пустого значения в поле номер карты.
    
 * Заполнение поля «Месяц»
    
    * Ввод `13` в поле месяц.
    * Ввод `0` в поле месяц.
    * Ввод спецсимвола в поле месяц.
    * Ввод буквы в поле месяц.
    * Ввод одной цифры в поле месяц.
    * Ввод пустого значения в поле месяц.
     
 * Заполнение поля «Год»
    
    * Ввод значения до текущего года в поле.
    * Ввод превышающего значения в `10` лет в поле год.
    * Ввод спецсимвола в поле год.
    * Ввод буквы в поле год.
    * Ввод одной цифры в поле год.
    * Ввод пустого значения в поле год.
 
* Заполнение поля «Владелец»
    
    * Ввод на кириллице в поле владелец.
    * Ввод спецсимвола в поле владелец.
    * Ввод цифры в поле владелец.
    * Ввод одной буквы в поле владелец.
    * Ввод более ста букв в поле владелец.
    * Ввод пустого значения в поле владелец.

* Заполнение поля «CVC/CVV»
    
    * Ввод символа в поле CVC/CVV.
    * Ввод буквы в поле CVC/CVV.
    * Ввод одной цифры в поле CVC/CVV.
    * Ввод двух цифр в поле CVC/CVV.
    * Ввод пустого значения в поле CVC/CVV.
 
* Отправка не заполненной формы

    * Ввод пустого значения в поле Номер карты.
    * Ввод пустого значения в поле Месяц.
    * Ввод пустого значения в поле Год.
    * Ввод пустого значения в поле Владелец.
    * Ввод пустого значения в поле CVC/CVV
    * Нажать `Продолжить`

## 2. Перечень используемых инструментов с обоснованием выбора.

* `Google Chrome` веб-браузер.

* `IntelliJ IDEA 2023.2.5 (Community Edition)` - интегрированная среда разработки программного обеспечения для многих языков программирования, в частности Java, JavaScript, Python.

* `Java JDK 11` объектно-ориентированный язык программирования общего назначения.

* `Gradle` cистема для автоматизации сборки приложений.

* `Selenide` библиотека для написания UI тестов.

* `Faker` библиотека  генерирует различные данные, подходящие для широкого спектра сценариев.

* `Lombok` библиотека сокращает объем стандартного кода в классах.

* `Git` и `GitHub` для совместной работы с кодом и настройки процесса непрерывной интеграции `GitHub Actions` так же можно использовать `AppVeyor`.

* `Docker`платформа, которая позволяет упаковать в контейнер приложение со всем окружением и зависимостями, а затем доставить и запустить его в целевой системе; способен запускать одновременно нескольких рабочих процессов с меньшим потреблением ресурсов, чем обычно; в качестве экономичной альтернативы виртуальным машинам.

* `Allure`– гибкий инструмент для составления отчетов о тестировании, который показывает понятное представление того, что было протестировано, в форме веб-отчета, но и позволяет всем участникам процесса разработки, извлекать полезную информации. Неудачные тесты можно разделить на ошибки и неработающие тесты, а также можно настроить журналы, шаги, приспособления, вложения, время.

## 3. Перечень и описание возможных рисков при автоматизации.

* Риск не работающего заявленного функционал приложения

* Увеличение времени на проектирование и реализацию автотестов из-за сложной внутренней стуктуры сайта, отсутствие тестовых меток `data test`для элементов страницы, если не к чему привязываться.

* Внесение изменений в БД, могут появиться ненужные тестовые данные.

* Увеличение нагрузки на сервер.

## 4. Интервальная оценка с учётом рисков в часах

* Изучение технического задания, подготовка  окружения проекта, подключение библиотек, зависимостей, запуск и изучение приложения – 15 часов.

* Разработка и написание плана автоматизации тестирования - 8 часов.

* Написания кода и отладка автотестов - 50 часов.

* Подготовка отчётных документов по итогам тестирования - 12 часов.

* Подготовка отчётных документов по итогам автоматизации - 4 часа.

## 5. План сдачи работ

* Проведены автотесты `28.04.2024`
* Отчётные документов по итогам тестирования `30.04.2024`
* Отчётные документов по итогам автоматизации `1.05.2024`

