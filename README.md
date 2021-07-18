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

Также для размещения служебных методов используется всякая разножопица вида: GlobalWeb, Global_<DevLogin>, <PartnerCompanyPrefix>_Tool, Dev_Base и подобные странные названия, понятные только автору.

Ограничения:

* разработчикам может быть запрещено изменять системные классы (включая global)
* в классе все методы должны иметь уникальные имена (хотя для статического метода и метода инстанса можно было бы разрешить одинаковые имена). В результате у многих Sys-классов мы видим странные имена для одних и тех же действий. Например, xSession.getDbSchema, Session.aosPort, Session::getAosPoart. никакой логики.

В данном проекте хотелось бы:

* создать несколько взаимосвязанных служебных методов и классов, которые будут логично сгруппированы
* статические методы разместить в Util-классах
* методы для работы с инстансами разместить в Sys-классах
* классам энумераторов добавлять суффикс Enumerator

Сейчас в проекте определены следующие классы:

* Any
* AnytypeUtil
* ArgsUtil
* ClrTypeUtil
* SessionUtil
* Enumerator
  * EnumeratorUtil
  * ConEnumerator
  * OneValueEnumerator
* Collection
  * ConUtil
  * ListUtil
  * SetUtil
* String
  * StrUtil
  * TextUtil - текст это "многострочная" строка
  * TextBufferUtil

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
