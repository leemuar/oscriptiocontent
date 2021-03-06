#С чего начать?

##Подготовка окружения

Здесь и далее будет предполагаться, что разработка ведется в среде Windows. Разработчики, использующие Linux и сами могут разобраться с настройкой окружения:)

### Минимально необходимые инструменты

* Клиент GIT ([msysgit](https://msysgit.github.io/) или [SourceTree](https://www.sourcetreeapp.com/))
* Visual Studio 2010-2013. Отлично подойдет бесплатная [VS 2013 Community Edition](https://www.visualstudio.com/en-us/news/vs2013-community-vs.aspx)

### Для сборки дистрибутивов

* [InnoSetup v.5](http://www.jrsoftware.org/isinfo.php) (для редактирования инсталлятора)
* [MSBuild Comunity Extension Pack v1.4](https://github.com/loresoft/msbuildtasks/releases)

## Получение исходных кодов

### Fork ###

* мы работаем через личные "форки", поэтому для разработки вам понадобится сделать FORK проекта
* сделайте личный fork и добавьте в него отдельным внешним репозиторием главный репозиторий - для удобства назовите его "base" или "upstream"
* все свои изменения помещайте вначале в личный fork

### назначение веток: ###

* master - стабильный код выпущенного релиза
* develop - код будущего релиза, находящегося в активной разработке.
* feature/* - код взятых в работу задач по созданию новой функциональности или рефакторингу существующей
* hotfix/* - код исправлений стабильного релиза, в случае если в релизе выявляются ОЧЕНЬ критичные ошибки
* 2.0 Enterprise - ветка планомерного и неблокирующего рефакторинга архитектуры проекта. Целью ветки является **incorporate alien technology**.

### Получение исходных кодов

Введите в командной строке:

    git clone https://bitbucket.org/<userName>/<forkName>.git
	
Будут склонированы исходные коды вашего форка на локальную машину. Далее, запускаете Visual Studio и изучаете проект, подглядывая в шпаргалку ["Как устроен проект"](page/Как%20устроен%20проект)

## Feature Branch ##

Мы работаем по процессу, который известен как **git-flow**. Неплохое описание этого процесса можно почитать по ссылкам:

* [http://habrahabr.ru/post/106912](http://habrahabr.ru/post/106912)
* [http://habrahabr.ru/post/159107](http://habrahabr.ru/post/159107)

При начале работы над новой функциональностью инициализируйте новую ветку по формату **feature/<name-of-feature>** на базе текущей ветки **develop** (в git-flow программы SourceTree это выполняется автоматически)
Не закрывайте ветку функциональности, пока Ваш pull-request не будет утвержден. 

## Test Driven Development ##

* при изменении поведения языка сначала пишите приемочные тесты на языке 1C/OneScript в формате [xUnitFor1C](https://github.com/xDrivenDevelopment/xUnitFor1C/wiki). Такая методика работы называется TDD (Test Driven Development)
* Организация тестирования описана в [Wiki организация тестирования](/docs/page/testing)
* примеры тестов находятся в каталоге .\tests репозитория и на [Wiki](/docs/page/testing)
* для версии 2.0 Enterprise также используйте стандартный фрэймворк MSTest - примеры можно просмотреть в отдельной ветке нашего репозитория

## Pull Request's ##

* при подаче pull-request'а имя вашей ветки разработки должно соответствовать целевой в головном репозитории
  * если вы работает над веткой **feature/some-feature** - целевой веткой тоже должна являться **feature/some-feature**
  * использование целевой ветки **develop** запрещено. такой pull-request не будет приниматься.
* каждый pull-request отрабатывает наш CI сервер на предмет стабильности по следующим шагам - Clean;Build;Tests;CreateInstall; и еще несколько специфичных шагов.
* Ваш pull-request может быть просмотрен и прокомментирован, поэтому отслеживайте изменения вашего pull-request
* Инициатор принятия вашего pull-request сливает (выполняет merge) из вашей ветки в ветку develop основного репозитария. После слияния ваш pull-request автоматически закрывается.