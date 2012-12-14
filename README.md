Badgenator
==========

Простой и удобный генератор бейджей

## Легенда
Одной маленькой компании понадобилось генерировать бейджи для своих нужд. Ну очень часто они печатали бейджи, кому-то нравилось прилепить себе чужое имя, кому-то нужно было чтобы его все узнавали.

Решено было сделать всё своими руками. Возможно это и было роковой ошибкой …

### Платформа
В качестве платформы была выбрана ОС [Ubuntu](http://www.ubuntu.com/). Там есть черная консоль и бегущий текст.

### Язык и Фреймворк
Решено было писать на [Ruby](http://www.ruby-lang.org/en/), версии не ниже 1.9.3 и конечно же использовать фреймворк [Ruby on Rails](http://rubyonrails.org/) самой последней версии, а именно 3.2.8.

**P.S.** А как же оформление!? Ну да, в качестве front-end фреймворка был использован [Bootstrap](http://twitter.github.com/bootstrap/).

### Инструментарий
Т.к. денег у них было не так уж много, решили, что редактором будет [SublimeText2](http://www.sublimetext.com/2).

## Генератор

### Что это?
Это приложение, в котором есть возможность создать сет (или набор), который можно наполнить бейджами. И сетом и бейджеми можно управлять. Создавать, удалять, менять и даже печатать. Загружать картинки. А так же загружать бейджи из файла.

### Пожалуйста, поподробнее об этом «Сете»
Под сетом подразумевается контейнер для бейджей.

### Какие у него есть атрибуты?
У сета всегда есть **название**. Может быть **картинка** и **источник** бейджей (файл содержащий в себе список бейджей).

![badge sets edit](https://github.com/Strech/badgenator_conf/raw/master/public/badgenator/badge_sets_edit.png)

**Название:** Это строка, длиной от 2 до 50 символов. Является обязательным атрибутом сета.

> **Внимание!** Если сет создается с файлом-источником, а его название пустое, то название должно быть сгенерировано из имени файла, без расширения.

**Картинка:**
Это изображение формата jpg, gif или png. При загрузке кроме оригинала должно формировать два размера - превью (thumb) и для показа в бейдже (badge). Наличие картинки является не обязательным.

**Источник:**
Файл со списком бейджей, это простой файл. Наличие файла является не обятельным.
Формат файла-источника следующий:

    <Имя>\t<Фамилия>\t<Компания>\t<Профессия>

> **Внимание!** Если в один сет загрузить два файла-источника, то бейджи должны быть только последнего загруженного.

### Что можно с ним делать?
Сет можно создавать, изменять, удалять, смотреть список сетов и печатать.

**Создание:** Это форма, состоящая из 3-х полей: название, картинка и источник. И 2-е кноки: Сохранить и Отмена.

Если все обязательные поля заполнены верно, то создается сет и мы попадаем на страницу со списком бейджей этого сета.

Если же закралась ошибка, то мы остаемся на странице создания сета и над формой видим красное поле с текстом ошибок, которые мы допустили.

**Изменение:** Это точно такая же форма как и при создании сета. Отличие только в том, что заполнено поле с названием сета и если была загружена картинка, то она должна показываться (размер badge), с возможностью ее удалить, не загружая новую.

Если все обязательные поля заполнены верно, то данные сета обновляются и мы попадаем на страницу со списком бейджей этого сета.

Если же закралась ошибка, то мы остаемся на странице изменения сета и над формой видим красное поле с текстом ошибок, которые мы допустили.

**Удаление:** При попытке удалить сет, должно появляться сообщение, а-ля «Точно-точно????» и при нажатии на кнопку «Ok» сет должен удалиться, а мы попасть на страницу со списком сетов.

> **Внимание!** Если удаляется сет, то с ним удаляются и все его бейджи (да, жизнь жестокая штука).

**Просмотр списка:** Все созданные сеты показываются в сводной таблице. Таблица имеет следующий формат:

    +----------+---------------+----------+
    | Картинка | Название сета | Действия |
    +----------+---------------+----------+
    |    …     |       …       |     …    |

> **Внмание!** Если сетов загружено много (более 20 шт.), то появляется постраничная навигация.

![badge sets index](https://github.com/Strech/badgenator_conf/raw/master/public/badgenator/badge_sets_index.png)

**Печать:** Это самая важная часть, т.к именно для этого и создавалось это приложение. Выводит список всех бейджей в сете и расставляет постраничные разрывы (для пейзажной печати это 4-е бейджа на страницу, для портретной печати это 3-и бейджа на страницу).

![badge sets print](https://github.com/Strech/badgenator_conf/raw/master/public/badgenator/badge_sets_print_1.png)

## Пожалуйста, поподробнее о «Бейджах»
Под бейджем подразумевается прямоугольник, в котором написано кто вы, где работаете и кем.

### Какие у него есть атрибуты?
У бейджа всегда есть **имя** и **компания**. Может быть **фамилия** и **профессия**.

![badges edit](https://github.com/Strech/badgenator_conf/raw/master/public/badgenator/badges_edit.png)

**Имя:** Это строка, длиной от 2 до 30 символов. Является обязательным атрибутом бейджа.  
**Фамилия:** Это строка, длиной от 2 до 30 символов. Является не обязательным атрибутом бейджа.  
**Компания:** Это строка, длиной от 3 до 30 символов. Является обязательным атрибутом.  
**Профессия:** Это строка, длиной от 3 до 30 символов. Является не обязательным атрибутом.  

> **Внимание!** Бейдж не может быть создан вне сета. Бейдж всегда принадлежит какому-то **одному** сету.

### Что можно с ним делать?
Бейдж можно создавать, изменять, удалять, смотреть бейдж, смотреть список бейджей.

**Создание:** Это форма, состоящая из 4-х полей: имя, фамилия, компания, профессия. И 2-е кноки: Сохранить и Отмена.

Если все обязательные поля заполнены верно, то создается бейдж и мы попадаем на страницу просмотра сета.

Если же в обязательные или не обязательные поля закралась ошибка, то мы остаемся на странице создания бейджа и над формой видим красное поле с текстом ошибок, которые мы допустили.

**Изменение:** Это точно такя же форма как и при создании бейджа. Отличие только в том, что все поля которые имеют значения уже заполнены.

Если все обязательные поля заполнены верно, то данные бейджа обновляются и мы попадаем на страну просмотра сета.

Если же в обязательные или не обязательные поля закралась ошибка, то мы остаемся на странице изменения бейджа и над формой видим красное поле с текстом ошибок, которые мы допустили.

**Удаление:** При попытке удалить бейдж, должно появляться сообщение, а-ля «Точно-точно????» и при нажатии на кнопку «Ok» бейдж должен удалиться, а мы попасть на страницу со списком бейджей.

> **Внимание!** Если удаляется последний бейдж, то с сетом ничего не происходит, он остается пустым (и одиноким).

**Просмотр одного бейджа:** Это отображение бейджа в том виде, в котором он идет на печать. В прямоугольник вписаны 4-е атрибута бейджа и скомпанованы таким образом Имя + Фамилия, Компания + Профессия.

![badges show](https://github.com/Strech/badgenator_conf/raw/master/public/badgenator/badges_show.png)

Так же присутствует изображение, которое было загружено для сета (размер badge), конечно, если оно имеется.

**Просмотр списка бейджей:** Все созданные бейджи для сета показываются в сводной таблице. Таблица имеет следующий формат:

    +-------+---------+-----+----------+-----------+----------+
    | Номер | Фамилия | Имя | Компания | Профессия | Действия |
    +-------+---------+-----+----------+-----------+----------+
    |   …   |    …    |  …  |     …    |     …     |     …    |

> **Внмание!** Если бейджей загружено много (более 5 шт.), то появляется постраничная навигация.

![badges index](https://github.com/Strech/badgenator_conf/raw/master/public/badgenator/badges_index.png)

## Как же запустить
На github.com нужно сделать форк репозитория https://github.com/Strech/badgenator_conf .

После этого у Вас появится свой репозиторий с адресом https://github.com/<ваш логин на github>/badgenator_conf.

На странице своего репозитория нужно зайти в раздел Settings -> Service Hooks и выбрать из списка Travis. 
В открывшейся форме указывается имя пользователя, Ваш персональный токен в системе Travis и галочка Active. 
Токен можно получить на сайте https://travis-ci.org/ на странице Вашего профиля после авторизации.

После этого можно клонировать репозиторий к себе на компьютер:
* cd ~/projects
* git clone git@github.com:<ваш логин на github>/badgenator_conf.git badgenator # ссылку можно найти на странице Вашего репозитория
* echo 'rvm use 1.9.3@badgenator' > badgenator/.rvmrc
* cd badgenator
* rake db:setup

### Запуск web-сервера
rails s

### Запуск тестов
rake db:test:prepare - при первом запуске или при изменениях в структуре данных.

rspec или rake - запуск всех тестов.

rspec spec/controllers - запуск определенного набора тестов.
