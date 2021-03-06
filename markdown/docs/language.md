#Описание языка сценариев

1Script поддерживает все возможности встроенного языка, перечисленные в ветке "Описание встроенного языка" стандартного синтакс-помощника.

* Нестрогая типизация
* Условия
* Циклы
* Исключения
* Доступ к массивам
* Доступ к COMОбъектам
* Встроенные функции работы с примитивными типами

Исключения из этого правила перечислены ниже.

## Отличия от стандартного языка 1С:

* Не реализовано динамическое выполнение кода функциями *Вычислить* и *Выполнить*
* Не реализованы функции *ДобавитьОбработчик*, *УдалитьОбработчик* для обработки событий COM-объектов.
* Не поддерживается оператор *Перейти* и метки
* Добавлена нестандартная директива препроцессора **#Использовать**, предназначенная для подключения [внешних библиотек](libraries).
* Не поддерживаются директивы препроцессора, как не имеющие особого смысла в скриптовой среде.
* Не используется механика "подсчета ссылок", принятая в 1С. Вместо этого применяется штатный сборщик мусора .NET. Это порождает непривычные специалисту 1С эффекты недетерминированного уничтожения объектов. Для явной очистки объектов введены функции:
  * ОсвободитьОбъект()
  * ВыполнитьСборкуМусора()

Некоторые отличия в будущем могут быть реализованы.

## Библиотека классов

OneScript содержит встроенную библиотеку классов и функций, совместимых с 1С:Предприятие.

О доступных классах и функциях см. раздел [Синтакс-помощник](/syntax)
