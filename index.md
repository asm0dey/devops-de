---
marp: true
title: "DevOps in DE: That's how we do it"
url: https://asm0dey.ru/p/devops-de
theme: gaia
size: 4K
class: default
paginate: true
footer: @asm0di0 at Twitter&emsp13;&emsp13;@asm0dey at Telegram&emsp13;&emsp13;#DevOops2020
---
<!--
_backgroundImage: "linear-gradient(to bottom, #000 0%, #1a2028 50%, #293845 100%)"
_class: lead
_color: white
_paginate: false
_footer: ""
-->

# <!-- fit --> DevOps in DE:
# <!-- fit --> That's how we do it

---
<!--
_backgroundImage: "linear-gradient(to bottom, #000 0%, #1a2028 50%, #293845 100%)"
_class: lead
_color: white
-->
# Кто я

- 14 лет в IT
- Сначала админ
- Потом разработчик
- Занимался DevOps до того, как это стало трендом :wink:
- Управлял разработчиками
- А потом *внезапно* стал дата инженером

---

<!--
_backgroundImage: "linear-gradient(to bottom, #000 0%, #1a2028 50%, #293845 100%)"
_class: lead
_color: white
-->
# <!-- fit --> Дата инженером? :scream:

---
<!--
_backgroundImage: "linear-gradient(to bottom, #000 0%, #1a2028 50%, #293845 100%)"
_color: white
-->
# <!-- fit --> Дата инженером? :scream:
* big learning
* machine data
* это не мы
---
<!--
_backgroundImage: "linear-gradient(to bottom, #000 0%, #1a2028 50%, #293845 100%)"
_color: white
-->
# А чем тогда?

- Поддержка инфраструктуры
- Архитектура системы хранения
- Автоматизация рутины
- ETL

---
<!--
_color: white
_class: lead
-->
<style scoped>
footer {
    color: white
}
</style>
![bg](images/Conqueror.webp)

# Вильгельм

---
<!-- _class: lead -->
![bg left:50% drop-shadow](images/man.svg)

# Это Вильгельм

Он занимается маркетингом

---
<!-- _class: lead -->
![bg right:50% drop-shadow](images/woman2.png)

# Это Элеонора

Она работает SRE

---
<!-- _class: lead -->
![bg left:50% drop-shadow](images/store.svg)

А это бизнес, который им платит

---
## Что нужно бизнесу

- Основной инструмент бизнеса — это эксель
- Из него можно подключиться к БД
- В него можно выгрузить данные из Google Analytics
- В нём можно посчитать всякие акдитории
- etc…

---
## Но со временем

- Количество данных растёт
- Становится сложно работать в одном файле
- Становится слишком много ручной работы

---
<!-- _class: lead -->
![bg drop-shadow](images/man.svg)
![bg vertical right:25% drop-shadow](images/woman2.png)
# Кажется, нам нужно хранилище данных!

---
<!-- 
_class: lead
_color: black
-->
![bg](images/hand.jpg)

# <!-- fit --> Что же делать? :scream:

---
# Hadoop!

- Бесплатно
- Умеет всё
- Можно купить версию с поддержкой
- *Никто* не умеет готовить

---
# Что значит «всё»?

- SQL
- NOSQL
- Файлы
- Движки запросов
- Движки ETL
- **YARN**!

---
<!-- _footer: "" -->
![bg fit](https://www.oreilly.com/library/view/apache-hive-essentials/9781788995092/assets/a64fec28-e2b2-42f0-96cf-098fe8385316.png)

---
## Шаг 1

1. Без паники
2. Открываем этот доклад
3. Ищем волшебное слово **«Ambari»**

---
### Ambari

Даёт нам простой (сравнительно) способ установки и настройки хадупа

```bash
yum install ambari-server*.rpm
ambari-server setup
ambari-server start
# agents
yum install ambari-agent*.rpm
ambari-agent start
```

---
## Шаг 2

1. Ставим HDFS
2. Ставим YARN
3. Ставим Hive
4. Заливаем данные
5. Начинаем делать запросы

---

# Бизнес растёт!
# ![h:200px drop-shadow](images/store.svg) ![drop-shadow h:500px right](images/store.svg)

---
<style scoped>
p:nth-child(1) > img:nth-child(1) { transform: scaleX(-1) }
</style>
# А что идёт рядом с бизнесом?

* Больше пользователей
* Больше данных
* Дата саентисты! :smiling_imp:
* Много ручной работы и много новых инструментов :worried:
* > ![box-shadow h:70](images/man.svg) Нам нужны инсайты! Нам нужны эксперименты!!1 :tm:
* Дата инженеры!

---
![bg](https://miro.medium.com/max/1416/1*WZks-LUukbigGIkcQL0h-g.jpeg)

---
# И внезапно…

Дата саентисты генерируют много кода.

Дата инженеры часто не имеют квалификации его проверить и времени его поддерживать.

**Время DevOps**

---
<style scoped>
ul,p {
    font-size: 85%
}
</style>

![bg right:25% drop-shadow](images/woman2.png)

# Звуки паники

Вопросы:
- Continuous integration
- Continuous delivery
- Frequent releases
- Automated rollback
- Automated testing
- Secured Process
- Monitoring

Courtesy of [@vvsevolovich](https://twitter.com/vvsevolodovich)

---
# Continuous integration

- Редко много народу работает над одним куском кода
- Все задачи достаточно сильно изолированы
- Нет больших причин усложнять ветвление

*И найти ошибки всё равно сложно*

---
![bg right:30% drop-shadow](images/woman2.png)

# План по DevOps

- :ballot_box_with_check: Continuous integration
- Continuous delivery
- Frequent releases
- Automated rollback
- Automated testing
- Secured Process
- Monitoring

---
<!-- _class: lead -->
# Continuous delivery

### Как пространство для фантазии

---
# Что нужно для CD?

- Миграция БД
- Выкатывать обновления
    *(без скандалов с заказчиков)*
- Откатывать обновления
- **Автоматизировать запуск**
- Способ протестировать то что сделал *(автоматически?)*
- Всё это должны делать люди, далёкие от администрирования

---
# Миграция БД

Production-ready решений нет!

Есть вопрос на реддите, где нет ответа :smile:

Поэтому пользуемся тем, что сделал я: [asm0dey/liquibase-hive](https://github.com/asm0dey/liquibase-hive)

Надеюсь что всё станет лучше :pray: