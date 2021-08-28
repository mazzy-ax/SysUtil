# SysUtil

[project]:https://github.com/mazzy-ax/SysUtil
[license]:https://github.com/mazzy-ax/SysUtil/blob/master/LICENSE
[ax2009]:ax2009
[ax2012]:ax2012
[ax4]:ax4
[axAssist]:http://www.axassist.com/

[SysUtil][project] &ndash; это служебные классы и методы, предназначенные для работы со стандартными типами и объектами в [Microsoft Dynamics AX 2009][ax2009]. Цель &ndash; облегчить разработку и чтение X++ кода.

## TODO ???

...как в чистой Аксапте, так и с установленным [axAssist]'ом.

Служебные классы позволяют сгруппировать полезные служебные методы в своеобразные namespace'ы.

В Аксапте есть три общепринятых способа размещать служебные методы в классах:

* в классе Global
* в Sys* классах (SysArgs, SysDataArea, SysDictTable, SysCLRType и т.д.)
* в *Util классах (AifUtil, AifWebReferenceUtil и еще несколько, могут содержать не только статические методы)

Также для размещения служебных методов используется всякая разножопица вида: GlobalWeb, Global_&lt;DevLogin&gt;, &lt;PartnerCompanyPrefix&gt;_Tool, Dev_Base и подобные странные названия, понятные только автору.

Ограничения:

* разработчикам может быть запрещено изменять системные классы (включая Global)
* в классе все методы должны иметь уникальные имена (хотя для статического метода и метода инстанса можно было бы разрешить одинаковые имена). В результате у многих Sys-классов мы видим странные имена для одних и тех же действий. Например:
  * xSession.getDbSchema - метод инстанса с префиксом get
  * Session.aosPort - метод инстанса без префикса get
  * Session::getAosPort - статический метод с префиксом get

В данном проекте хотелось бы:

* создать несколько взаимосвязанных служебных методов и классов, которые будут логично сгруппированы
* статические методы разместить в Util-классах
* методы для работы с инстансами разместить в Sys-классах
* классам энумераторов добавлять суффикс Enumerator

Сейчас в проекте определены следующие классы:

* [Error](./Src/Error)
  * [Error](./Src/Error/Class_Error.xpp)
* [Any](./Src/Any)
  * [Any](./Src/Any/Class_Any.xpp)
  * [AnytypeUtil](./Src/Any/Class_AnytypeUtil.xpp)
* [Types](./Src/Types)
  * [DictTypeUtil](./Src/Types/Class_DictTypeUtil.xpp)
  * [ExtendedTypeIdUtil](./Src/Types/Class_ExtendedTypeIdUtil.xpp)
  * [TypeUtil](./Src/Types/Class_TypeUtil.xpp)
* [CLR](./Src/CLR)
  * [ClrTypeUtil](./Src/CLR/Class_ClrTypeUtil.xpp)
* [Str](./Src/Str)
  * [StrUtil](./Src/Str/Class_StrUtil.xpp)
  * [TextBufferUtil](./Src/Str/Class_TextBufferUtil.xpp)
  * [TextUtil](./Src/Str/Class_TextUtil.xpp) &mdash; текст это "многострочная" строка
* [Collection](./Src/Collection)
  * [ArrayUtil](./Src/Collection/Class_ArrayUtil.xpp)
  * [CollectionUtil](./Src/Collection/Class_CollectionUtil.xpp)
  * [ConUtil](./Src/Collection/Class_ConUtil.xpp)
  * [ListUtil](./Src/Collection/Class_ListUtil.xpp)
  * [MapUtil](./Src/Collection/Class_MapUtil.xpp)
  * [SetUtil](./Src/Collection/Class_SetUtil.xpp)
  * [StackUtil](./Src/Collection/Class_StackUtil.xpp)
  * [StructUtil](./Src/Collection/Class_StructUtil.xpp)
* [Enumerator](./Src/Enumerator)
  * [ArrayEnumerator](./Src/Enumerator/Class_ArrayEnumerator.xpp)
  * [ConEnumerator](./Src/Enumerator/Class_ConEnumerator.xpp)
  * [EnumeratorUtil](./Src/Enumerator/Class_EnumeratorUtil.xpp)
  * [OneValueEnumerator](./Src/Enumerator/Class_OneValueEnumerator.xpp)
  * [RecordEnumerator](./Src/Enumerator/Class_RecordEnumerator.xpp)
  * [StrSplitEnumerator](./Src/Enumerator/Class_StrSplitEnumerator.xpp)
* [Class](./Src/Class)
  * [ClassIdUtil](./Src/Class/Class_ClassIdUtil.xpp)
  * [DictClassUtil](./Src/Class/Class_DictClassUtil.xpp)
  * [ObjectUtil](./Src/Class/Class_ObjectUtil.xpp)
* [Record](./Src/Record)
  * [DictTableUtil](./Src/Record/Class_DictTableUtil.xpp)
  * [RecordList](./Src/Record/Class_RecordList.xpp)
  * [RecordMap](./Src/Record/Class_RecordMap.xpp)
  * [RecordUtil](./Src/Record/Class_RecordUtil.xpp)
  * [SysRecordInsertList](./Src/Record/Class_SysRecordInsertList.xpp)
  * [TableIdUtil](./Src/Record/Class_TableIdUtil.xpp)
* [Field](./Src/Field)
  * [DictFieldUtil](./Src/Field/Class_DictFieldUtil.xpp)
  * [FieldIdUtil](./Src/Field/Class_FieldIdUtil.xpp)
* [Misc](./Src/Misc)
  * [Args](./Src/Misc/Args)
    * [ArgsUtil](./Src/Misc/Args/Class_ArgsUtil.xpp)
  * [Query](./Src/Misc/Query)
    * [QueryRunUtil](./Src/Misc/Query/Class_QueryRunUtil.xpp)
    * [SysQuery](./Src/Misc/Query/Class_SysQuery.xpp)
  * [Session](./Src/Misc/Session)
    * [SessionUtil](./Src/Misc/Session/Class_SessionUtil.xpp)
  * [Timer](./Src/Misc/Timer)
    * [SysStopwatch](./Src/Misc/Timer/Class_SysStopwatch.xpp)
    * [Timer](./Src/Misc/Timer/Class_Timer.xpp)
  * [PrevCurr](./Src/Misc/Class_PrevCurr.xpp)

## CodeStyle

В целом, используются [стандарты, принятые в Аксапте](https://docs.microsoft.com/en-us/dynamicsax-2012/developer/x-coding-standards)

Отличия от стандарта:

* механизм меток не используется, текст сообщений вставлен "как есть".
* `xmldoc` не используется из за того, что человеку сложно прочесть код и `xmldoc`-комментарий в коде.
* `markdown`-разметка в комментариях допускается. Проект javadoc+markdown+xmlddoc приветствуется.
* комментарии и тексты, предназначенные для чтения человеком, пишутся в основном на русском языке. Русскоязычные аксаптоведы, велкам.
  * однако, если есть предположение, что текст сообщения может пойти через интернет или через устройства, где возможны ошибки кодировки, то тексты нужно писать символами в кодировке ASCII. Например, класс `error` возвращает текст ошибок на английском.
* в комментариях в публичном проекте допускается
  * использовать Javadoc тэги. См. [Javadoc Tag Conventions](https://www.oracle.com/technical-resources/articles/java/javadoc-tool.html#tag)
  * писать имена авторов, которые работали над кодом. См.также [Javadoc @author tag good practices](https://stackoverflow.com/questions/17269843/javadoc-author-tag-good-practices) и [Stop using Javadoc @author tag](https://www.vojtechruzicka.com/stop-using-javadoc-author-tag/).
  * указывать даты и версии (в том числе в тэге `@since`)
* по возможности, оператор `return` возвращает переменную, а не выражение. Возвращаемые переменные могут использоваться при отладке, когда нужно подменить возвращаемое значение.
* в версиях ax2009- после блока объявления переменных обязательно нужно вставлять дополнительную `;`, если следующий код начинается не с ключевого слова. Это правило позволяет избежать ошибок, если в Аксапте кто-то уже создал таблицу-класс-тип-enum с таким именем.
* да, я знаю о своей привычке `if( operator )` вместо принятого `if (operator)`. Однако, когда мне нужно писать по стандарту, то скорость создания кода у меня падает настолько, что я отказался от переучивания. Извините. Проект с форматером кода приветствуется.

## Disclaimer

* Названия классов и методов в пререлизах проекта скорее всего будут меняться.
* Код в xpp-файлах конвертирован из xpo только для удобства использования человеком. Оригиналом является код в xpo-проектах, отличия между xpo и xpp всегда трактуются в пользу текста из xpo-проектов.
* Проект опубликован "как есть" под лицензией [MIT][license]: вы можете использовать данный код как угодно безо всяких отчислений, автор не дает никаких гарантий и не несет ответственности за возможный эффект от использования кода на проектах.

## Прочее

* проект сознательно сделан для классических версий Аксапты
* в проекте сознательно не используется xmldocs
* README и комментарии сознательно сделаны на русском языке
* тексты записаны простой строкой на русском языке и не используют меток

## ChangeLog

Проект находится в состоянии альфа версии &ndash; названия и состав еще не устаканились. Возможны серьезные изменения.

* [CHANGELOG.md](CHANGELOG.md)
* <https://github.com/mazzy-ax/SysUtil/releases>

## Помощь проекту

Буду признателен вашим замечания, предложения и советы по проекту в разделе [Issues](https://github.com/mazzy-ax/SysUtil/issues) по поводу:

* имен методов и классов
* code style в проекте
* unit-тестов
* описания методов и документации

Также буду признателен вашим донатам на развитие проекта.

Мазуркин Сергей (mazzy)
