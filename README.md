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

* [Any/](./ax2009/Src/Any)
  * [Any.xpp](./ax2009/Src/Any/Class_Any.xpp)
  * [AnyPrevCurrent.xpp](./ax2009/Src/Any/Class_AnyPrevCurrent.xpp)
  * [AnytypeUtil.xpp](./ax2009/Src/Any/Class_AnytypeUtil.xpp)
* [Args/](./ax2009/Src/Args)
  * [ArgsUtil.xpp](./ax2009/Src/Args/Class_ArgsUtil.xpp)
* [CLR/](./ax2009/Src/CLR)
  * [ClrTypeUtil.xpp](./ax2009/Src/CLR/Class_ClrTypeUtil.xpp)
* [Collection/](./ax2009/Src/Collection)
  * [ConUtil.xpp](./ax2009/Src/Collection/Class_ConUtil.xpp)
  * [ListUtil.xpp](./ax2009/Src/Collection/Class_ListUtil.xpp)
  * [SetUtil.xpp](./ax2009/Src/Collection/Class_SetUtil.xpp)
* [Enumerator/](./ax2009/Src/Enumerator)
  * [ConEnumerator.xpp](./ax2009/Src/Enumerator/Class_ConEnumerator.xpp)
  * [EnumeratorUtil.xpp](./ax2009/Src/Enumerator/Class_EnumeratorUtil.xpp)
  * [OneValueEnumerator.xpp](./ax2009/Src/Enumerator/Class_OneValueEnumerator.xpp)
* [Error/](./ax2009/Src/Error)
  * [Error.xpp](./ax2009/Src/Error/Class_Error.xpp)
* [Query/](./ax2009/Src/Query)
  * [QueryRunUtil.xpp](./ax2009/Src/Query/Class_QueryRunUtil.xpp)
  * [SysQuery.xpp](./ax2009/Src/Query/Class_SysQuery.xpp)
* [Record/](./ax2009/Src/Record)
  * [RecordUtil.xpp](./ax2009/Src/Record/Class_RecordUtil.xpp)
  * [SysRecordInsertList.xpp](./ax2009/Src/Record/Class_SysRecordInsertList.xpp)
  * [SysRecordList.xpp](./ax2009/Src/Record/Class_SysRecordList.xpp)
  * [SysRecordMap.xpp](./ax2009/Src/Record/Class_SysRecordMap.xpp)
* [Session/](./ax2009/Src/Session)
  * [SessionUtil.xpp](./ax2009/Src/Session/Class_SessionUtil.xpp)
* [Str/](./ax2009/Src/Str)
  * [StrUtil.xpp](./ax2009/Src/Str/Class_StrUtil.xpp)
  * [TextBufferUtil.xpp](./ax2009/Src/Str/Class_TextBufferUtil.xpp)
  * [TextUtil.xpp](./ax2009/Src/Str/Class_TextUtil.xpp) &ndash; текст это "многострочная" строка
* [SysDict/](./ax2009/Src/SysDict)
  * [SysDictClass.xpp](./ax2009/Src/SysDict/Class_SysDictClass.xpp)
  * [SysDictEnum.xpp](./ax2009/Src/SysDict/Class_SysDictEnum.xpp)
  * [SysDictTable.xpp](./ax2009/Src/SysDict/Class_SysDictTable.xpp)
* [Timer/](./ax2009/Src/Timer)
  * [SysStopwatch.xpp](./ax2009/Src/Timer/Class_SysStopwatch.xpp)
  * [Timer.xpp](./ax2009/Src/Timer/Class_Timer.xpp)

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
