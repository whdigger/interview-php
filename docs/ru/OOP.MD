### 1. Что вообще такое ООП - на каких постулатах оно построено.

<details>
    <summary>Инкапсуляция, Наследование, Полиморфизм, Абстракция, Композиция</summary>

1. Инкапсуляция – принцип сокрытия данных и методов от общего доступа. Минимизация связей между классами.
2. Наследование – пораждение одного класса от другого, с возможностью переопределения или расширения методов.
3. Полиморфизм – означает, что объекты различных классов могут иметь общий интерфейс, но могут вести себя по-разному.
   Реализовывается через интерфейсы.
4. Абстракция – представление объекта или концепции на высоком уровне абстракции, скрывая детали реализации. Она
   позволяет создавать абстрактные классы и интерфейсы, которые определяют общий контракт для классов-наследников
5. Композиция – представляет собой процесс создания более сложных объектов путем объединения более простых объектов. Это
   позволяет создавать объекты, состоящие из других объектов, и устанавливать отношения между ними.

</details>

### 2. Какие паттерны и антипатерны программирования вы знаете и какие использовали в работе.

<details>
    <summary>Порождающие: Abstract Factory, Builder, Simple Factory, Static Factory, Factory Method </summary>

**Abstract Factory**
Создаёт связанные или зависимые объекты без указания конкретных классов. Клиент не заботиться как создаются объекты,
он только заботиться как они сочетаются друг с другом

Создание для разных ОС способов создания отображения данных. 

**Builder**
Интерфейс для производства частей сложного объекта.

Построитель запросов для query

**Simple Factory**
Используется для создания объекта внутри метода

**Static Factory**
Используется для создания объектов определенного типа, скрывая детали конкретной реализации создания объектов от клиента.

Конструирование сундуков с различными видами артефактов.
Создание различных видов социальных ресурсов для получения информации о счётчиках

**Factory Method**
Метод для создания объектов, в простых случаях, этот абстрактный класс может быть только интерфейсом.

</details>

<details>
    <summary>Структурные: Adapter, Bridge, Data Mapper, Decorator, DI, Facade, Proxy, Registry </summary>

**Adapter**

Используется для преобразования интерфейса одного класса в интерфейс, ожидаемый другим классом
Единый интерфейс для работы с различными БД (mysql, postresql, interbase)

Может использоваться как создание своего интерфейса и использование при расширение поведения.

**Bridge**

Используется для отделения абстракции от её реализации так, что они могли изменяться независимо друг от друга.

Пример реализация разных сервисов с зависимостью от интерфейсов

**Data Mapper**

Выступает в роли посредника для двунаправленной передачи данных между постоянным хранилищем данных 
(часто, реляционной базы данных) и представления данных в памяти.

Пример реализация разных ORM

**Decorator**
Для динамического добавления новых функциональностей или изменения поведения объекта без изменения его основной структуры.

Реализация различного рода скидок в корзине пользователя, система отправки уведомлений с различными каналами для которой
необходимо шифровать сообщения.

**DI**
Для реализации слабосвязанной архитектуры. Чтобы получить более тестируемый, сопровождаемый и расширяемый код.

**Facade**
Фасад предназначен для разделения клиента и подсистемы путем внедрения многих (но иногда только одного) интерфейсов
и, конечно, уменьшения общей сложности.

**Proxy**
Использование для кеширования объектов, управления доступом, кеширования, ленивой инициализации и других сценариев

**Registry**
Для реализации централизованного хранения объектов, часто используемых во всем приложении, как правило,
реализуется с помощью абстрактного класса только c статическими методами

</details>


<details>
    <summary>Поведенческие: Strategy, Event, Null Object, Command </summary>

**Strategy**
Работа приложения с различными типами конфигурационных файлов (XML, YAML, PHP array), системы обработки платежей,
системы для отправки уведомлений

**Event**
Уведомление подписчиков на различные события отправка нотификации через (email, sms ...)
</details>

<details>
    <summary>Hydrator, DTO</summary>

**Hydrator**
Для преобразования данных из одного формата в другой, обычно для заполнения объектов данными из источников данных, таких
как базы данных или API.

ORM (Object-Relational Mapping), Формы и валидация, Сериализация и десериализация (json, XML, cvs)

**DTO**
Используется для передачи данных между компонентами системы или между слоями приложения

API разработка, Интеграция с внешними системами, передачи данных между клиентом и сервером
</details>

### 3. Что такое принципы SOLID

<details>
    <summary>Single responsibility, Open-closed, Liskov substitution, Interface segregation и Dependency inversion</summary>

1. **Single responsibility** - На каждый объект должна быть возложена одна единственная обязанность
2. **Open-closed** - Программные сущности должны быть открыты для расширения, но закрыты для модификации
3. **Liskov substitution** - Объекты в программе могут быть заменены их наследниками без изменения поведения программы
4. **Interface segregation** - Много специализированных интерфейсов лучше, чем один универсальный
5. **Dependency inversion** - Зависимости внутри системы строятся на основе абстракций. Модули верхнего уровня не
   зависят от модулей нижнего уровня. Абстракции не должны зависеть от деталей. Детали должны зависеть от абстракций (
   зависимости должны строится относительно абстракций, а не деталей)

</details>

### 4. Что такое статический метод. Где лучше использовать вызов статических методов, в каких патернах используются?

Это метод, который принадлежит классу, а не экземпляру объекта.
Лучше всего использовать когда не требуется доступ к состоянию конкретного экземпляра класса.

Основные особенности статических методов:

- Они не могут обращаться к нестатическим свойствам или методам класса напрямую, только к другим статическим свойствам
  или методам.
- Они обычно используются для глобальных операций, общих для всех экземпляров класса, и не зависят от конкретного
  состояния объекта.

Factory Method, Singleton, Adapter

### 5. Что такое позднее статическое связывание как происходит как используется слово static и можно ли его переопределять

Это механизм в объектно-ориентированных языках программирования, который позволяет обрабатывать вызовы статических
методов или свойств в контексте наследников.
Да переопределять можно

### 6. Что такое DI, как работает, для чего он нужен.

**DI (Dependency Injection)** - это паттерн проектирования, который используется для управления зависимостями между
объектами. Он позволяет внедрять зависимости в объекты извне, вместо того чтобы создавать их внутри объектов самостоятельно.

Преимущества использования DI в PHP:

1. **Упрощение тестирования**: DI позволяет легко подменять зависимости объектов на моки или заглушки в тестах, что
   упрощает их изоляцию и проверку.
2. **Повышение переиспользуемости**: Объекты становятся более независимыми и переиспользуемыми, поскольку их зависимости
   могут быть заменены без изменения самого объекта.
3. **Снижение связанности**: Зависимости объявляются в явном виде, что уменьшает связанность между объектами. Это делает
   код более гибким и легко поддающимся изменениям.
4. **Читаемость и понятность**: Когда зависимости передаются явно через конструктор или сеттеры, код становится более
   понятным и читаемым. Зависимости становятся явными, и легче понять, какие компоненты взаимодействуют между собой.

### 6. Чем отличается DI и IOC

**IoC** - это широкий принцип проектирования, который определяет, что контроль над потоком выполнения программы должен
быть передан внешнему компоненту или контейнеру.
Вместо того, чтобы объекты создавали и управляли своими зависимостями самостоятельно, они получают свои зависимости из
внешнего источника.
Таким образом, контроль над созданием и управлением объектов передается контейнеру или фреймворку, что позволяет легко
внедрять зависимости в объекты.

**DI** - это конкретная реализация IoC, где зависимости передаются в объекты, обычно через конструкторы, сеттеры или
методы-инъекторы. DI помогает обеспечить инверсию контроля и упрощает управление зависимостями между объектами.

### 7. Dependency injection vs dependency inversion

**Dependency Injection (внедрение зависимостей)** - это техника, которая позволяет классу получать зависимости извне,
вместо того, чтобы создавать их самому. Передаются через конструкторы, сеттеры или методы класса.
Это делает классы более гибкими, модульными и тестируемыми, поскольку зависимости могут быть заменены или имитированы
для тестирования или изменения поведения класса. DI помогает снизить связность и повысить переиспользуемость
компонентов.

**Dependency Inversion (инверсия зависимостей)** - это принцип, предложенный в SOLID-принципах программирования, который
гласит, что классы должны зависеть от абстракций, а не от конкретных реализаций.
Это означает, что высокоуровневые модули не должны зависеть от низкоуровневых модулей, а оба типа модулей должны
зависеть от абстракций.

### 8. Что такое рефлексия и для чего нужна?

Рефлексия (reflection) - это механизм, который позволяет программе анализировать и модифицировать свою структуру во
время выполнения.
Может быть полезен во многих случаях, таких как создание гибких фреймворков, анализ и изменение кода во время
выполнения, реализация динамической интеграции

### 9. Композиция, агрегация когда какой лучше применять?

**Композиция**
"Has-A Relationship" это отношение означает, что один объект является составной частью другого объекта и время жизни "
части" зависит от времени жизни целого.

**Агрегация**
"Part Of Relationship" если же один объект получает ссылку (указатель) на другой объект в процессе конструирования.

Композиция проще с точки зрения клиентов класса, но налагает определенные ограничения: "целое" должно уметь создавать "
составную часть".
Агрегация гибче, но налагает другие ограничения: теперь "целое" не скрывает о существовании "составной части", а значит
и не сможет заменить ее на другую "составную часть" в будущем.
<details>
    <summary>Заметка</summary>
Большое количество наследования говорит о том, что проектировщики забыли о старом добром совете Банды Четырех, который сводится к тому, что следует предпочесть агрегацию наследованию, поскольку первая дает большую гибкость и динамичность во время исполнения.

Обилие же композиции говорит о нарушении Принципа Инверсии Зависимостей, сформулированном Бобом Мартином, которую сейчас
можно выразить в терминах агрегации и композиции: предпочитайте агрегацию вместо композиции, поскольку первая
стимулирует использование абстракций, а не конкретных классов.
</details>

### 10. Патерны распределённых систем?

- 2PC (Two-Phase Commit)

**Фаза подготовки (Prepare Phase):**
  Координатор отправляет запрос на подготовку (PREPARE) всем узлам

**Фаза фиксации (Commit Phase):**
  В зависимости от ответов в фазе подготовки, координатор решает, следует ли фиксировать (COMMIT) или откатывать (ROLLBACK) транзакцию и ответ об успешности

_Изолированность транзакций_

- Saga

**Инициирование:**
  Глобальная транзакция инициируется запросом пользователя или внешним событием.

**Запуск локальных транзакций:**
  Сага включает локальные транзакции, каждая из которых представляет собой действие, выполняемое одним из сервисов.

**Компенсирующие Действия:**
  В случае ошибки в одной из локальных транзакций, срабатывают компенсирующие действия для отмены изменений.

**Успешное Завершение:**
  Если все локальные транзакции успешно завершились, сага считается успешной, и изменения фиксируются.

**Обработка Ошибок:**
  В случае ошибки в любой локальной транзакции, Saga может применить компенсирующие действия для восстановления системы в согласованное состояние.

_Нет изолированности_

_Решать проблему согласованности в распределенных транзакциях_

### 11. PSR

- Авто загрузка
- HTTP интерфейсы (Response, Request)
- Интерфейсы (DI, Loger, Event dispatcher)
- Стилистика кода

### 12. Зацепления и высокая связаность, в чём отличия?

Зацепление (coupling) описывает степень взаимосвязи и зависимости между компонентами системы. Чем выше зацепление, тем
сильнее компоненты связаны друг с другом. Высокое зацепление может приводить к проблемам, таким как сложность изменений,
трудности восприятия и повторного использования кода. Идеальным является слабое зацепление, когда компоненты системы
имеют минимальную зависимость друг от друга.

Высокая связанность (cohesion) описывает степень, в которой элементы внутри компонента связаны и сфокусированы на одной
задаче. Высокая связанность означает, что компонент выполняет свои функции без излишней зависимости от других
компонентов. Высокая связанность способствует лучшей модульности, повышает понятность и повторное использование кода.

Важно стремиться к слабому зацеплению и высокой связанности при проектировании микросервисов, чтобы обеспечить легкость
разработки, изменений и масштабируемости системы.

### 13. Приведи пример использования open-close принципа на паттернах
 
- Использование интерфейса для расширения и закрыт для модификации
- Декоратор, Мост, Адаптер, Стратегия

[Назад](../../README.md)