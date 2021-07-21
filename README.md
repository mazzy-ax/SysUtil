# SysUtil

[project]:https://github.com/mazzy-ax/SysUtil
[license]:https://github.com/mazzy-ax/SysUtil/blob/master/LICENSE
[ax2009]:ax2009
[ax2012]:ax2012
[ax4]:ax4
[axAssist]:http://www.axassist.com/

[SysUtil][project] &ndash; это служебные классы и методы, предназначенные для работы со стандартными объектами в [Microsoft Dynamics AX 2009][ax2009]. Цель &ndash; облегчить разработку на X++ как в чистой Аксапте, так и с установленным [axAssist]'ом.

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

* [Any/](./Src/Any)
  * [Any.xpp](./Src/Any/Class_Any.xpp)
  * [AnyPrevCurrent.xpp](./Src/Any/Class_AnyPrevCurrent.xpp)
  * [AnytypeUtil.xpp](./Src/Any/Class_AnytypeUtil.xpp)
* [Args/](./Src/Args)
  * [ArgsUtil.xpp](./Src/Args/Class_ArgsUtil.xpp)
* [CLR/](./Src/CLR)
  * [ClrTypeUtil.xpp](./Src/CLR/Class_ClrTypeUtil.xpp)
* [Collection/](./Src/Collection)
  * [ConUtil.xpp](./Src/Collection/Class_ConUtil.xpp)
  * [ListUtil.xpp](./Src/Collection/Class_ListUtil.xpp)
  * [SetUtil.xpp](./Src/Collection/Class_SetUtil.xpp)
* [Enumerator/](./Src/Enumerator)
  * [ConEnumerator.xpp](./Src/Enumerator/Class_ConEnumerator.xpp)
  * [EnumeratorUtil.xpp](./Src/Enumerator/Class_EnumeratorUtil.xpp)
  * [OneValueEnumerator.xpp](./Src/Enumerator/Class_OneValueEnumerator.xpp)
* [Error/](./Src/Error)
  * [Error.xpp](./Src/Error/Class_Error.xpp)
* [Query/](./Src/Query)
  * [QueryRunUtil.xpp](./Src/Query/Class_QueryRunUtil.xpp)
  * [SysQuery.xpp](./Src/Query/Class_SysQuery.xpp)
* [Record/](./Src/Record)
  * [RecordUtil.xpp](./Src/Record/Class_RecordUtil.xpp)
  * [SysRecordInsertList.xpp](./Src/Record/Class_SysRecordInsertList.xpp)
  * [SysRecordList.xpp](./Src/Record/Class_SysRecordList.xpp)
  * [SysRecordMap.xpp](./Src/Record/Class_SysRecordMap.xpp)
* [Session/](./Src/Session)
  * [SessionUtil.xpp](./Src/Session/Class_SessionUtil.xpp)
* [Str/](./Src/Str)
  * [StrUtil.xpp](./Src/Str/Class_StrUtil.xpp)
  * [TextBufferUtil.xpp](./Src/Str/Class_TextBufferUtil.xpp)
  * [TextUtil.xpp](./Src/Str/Class_TextUtil.xpp) &ndash; текст это "многострочная" строка
* [SysDict/](./Src/SysDict)
  * [SysDictClass.xpp](./Src/SysDict/Class_SysDictClass.xpp)
  * [SysDictEnum.xpp](./Src/SysDict/Class_SysDictEnum.xpp)
  * [SysDictTable.xpp](./Src/SysDict/Class_SysDictTable.xpp)
* [Timer/](./Src/Timer)
  * [SysStopwatch.xpp](./Src/Timer/Class_SysStopwatch.xpp)
  * [Timer.xpp](./Src/Timer/Class_Timer.xpp)

## Disclaimer

* Названия классов и методов в пререлизах проекта скорее всего будут меняться.
* Код в xpp-файлах конвертирован из xpo только для удобства использования человеком. Оригиналом является код в xpo-проектах, отличия между xpo и xpp всегда трактуются в пользу текста из xpo-проектов.
* Проект выложен "как есть" под лицензией [MIT][license]: вы можете использовать данный код как угодно безо всяких отчислений, автор не дает никаких гарантий и не несет ответственности за возможный эффект от использования кода на проектах.

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
