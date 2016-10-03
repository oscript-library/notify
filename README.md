# Описания оповещений

Библиотека предназначена для создания и обработки объектов ОписаниеОповещения.

Синтаксис создания объектов максимально приближен к синтаксису 1С:Предприятие 8.

## Возвожности

* Задание модуля и процедуры для описания оповещения
* Передача произвольного параметра "ДополнительныеПараметры" в процедуру (опционально)
* Задание обработчиков ошибки при выполнении оповещения (опционально)

## Использование

```bsl
// Подключение библиотеки
#Использовать notify

// Процедура-обработчик описания оповещения.
//
Процедура СообщитьПриветМир(Результат, ДополнительныеПараметры = Неопределено) Экспорт
    Сообщить("Привет, " + ДополнительныеПараметры + "!");
    ВызватьИсключение "Что-то произошло!";
КонецПроцедуры

// Процедура-обработчик ошибки.
//
Процедура ОбработкаОшибки(ИнформацияОбОшибке, СтандартнаяОбработка, ДополнительныеПараметры) Экспорт
    Сообщить("Шеф, усё пропало!");
    Сообщить("Информация об ошибке: " + ИнформацияОбОшибке);
КонецПроцедуры

// Создание объекта ОписаниеОповещения. Аналогично использованию "Новый ОписаниеОповещения("СообщитьПриветМир", ЭтотОбъект)" в 1С.
ОписаниеОповещения = ОписанияОповещений.Создать("СообщитьПриветМир", ЭтотОбъект, "Мир", "ОбработкаОшибки", ЭтотОбъект);

// Выполнение обработки оповещения. Аналогично использованию ВыполнитьОбработкуОповещения(ОписаниеОповещения) в 1С.
ОписанияОповещений.ВыполнитьОбработкуОповещения(ОписаниеОповещения);
```

