### 1. Что выведет данная программа, рассуждение в слух

```php
function recur($i)
{
    if ($i <= 100) {
        print $i;
        recur(++$i);
        print $i;
    }
}
recur(99);

99
100
101
100
```

### 2. Есть такие куски кода, что в нём не так, как его можно улучшить и почему

```php
namespace Demo;

use DB;

class OrdersReport
{
    public function getOrdersInfo($startDate, $endDate)
    {
        $orders = $this->queryDBForOrders($startDate, $endDate);
        return $this->format($orders);
    }

    protected function queryDBForOrders($startDate, $endDate)
    {
        return DB::table('orders')->whereBetween('created_at', [$startDate, $endDate])->get();
    }

    protected function format($orders)
    {
        return '<h1>Orders: ' . $orders . '</h1>';
    }
}
```

```php

interface workerInterface
{
    public function work();

    public function sleep();
}

class HumanWorker implements workerInterface
{
    public function work()
    {
        var_dump('works');
    }

    public function sleep()
    {
        var_dump('sleep');
    }
}

class RobotWorker implements workerInterface
{
    public function work()
    {
        var_dump('works');
    }

    public function sleep()
    {
        // No need
    }
}
```

### 3. Задача на поиск суммы двух чисел в массиве.

**Условие**:
Функция принимает на вход массив чисел, и число Х, на выход отдает два индекса, числа по которым в сумме дают Х.
Если таких нет - то -1, -1.

**Пример**:
Дано: [1, 7, 3] 4
Результат: [0, 2]

```php
$array = [1, 7, 3];
function ($array, $find) {
    $hashmap = [];
    
    foreach ($array as $index => $value) {
        $hash = $find - $value;
        
        if ($hashmap[$hash] ){
            return [$hashmap[$hash], $index]
        }
        $hashmap[$value] = $index;
    }
}
```

### 4. У тебя есть скрипт к которому одномоментно могут обратиться 100 запросов тебе нужно разрулить их

Необходимо использовать ключ в кеш и проверять занят ли скрипт в текущее время

### 5. Что будет напечатано?

```php
var_dump((int) ('2test') . (int) ('test') );
var_dump((int) ('test2') . (int) ('test') );

20
00
```

```php
1 << 3
```

### 6. Что выведет программа

```php
$a = [1,2,3];
$b = [2,3,4];
foreach ($a as &$value)
    ++$value;
foreach ($b as $value)
    ++$value;
var_dump($a);
var_dump($b);
```

### 7. Дорабатать и развивать уже готовый проект

Через неделю Вашего знакомства с проектом, маркетинговый отдел запустил довольно успешную кампанию и время загрузки
сайта за сутки увеличилось с 0.5c до 15с. Как вы будете решать проблему?

- Посмотрю на вывод SHOW PROCESSLIST; в консоли MySQL на кол-во и время выполнения запросов.
- Хорошо. Допустим, там постоянно висит 2-3 различных запроса с большим временем выполнения. Ваши действия?
- Оптимизация базы, индексы, объединения, запросы 
- Ок, а если много различных запросов с небольшим временем выполнения?
- Необходимо использовать кэширование запросов
- Ок, допилили кэширование, но проблема все же осталась
- Некорректная работа кэширующего механизма?
- Допустим. Давайте немного скорректируем условия - вы открываете консоль MySQL и видите там обычное кол-во запросов. В чем ещё может быть проблема?
- Долгие запросы к сторонним ресурсам, проблемы на стороне выполнения скрипта.

### 8. Что выведет на экран скрипт в результате?

```php
class Foo {
    public $test = NULL;
}
$foo = new Foo;
$foo->test = '12345678';
$bar = $foo;
$bar->test = '87654321';
echo $foo->test;
```
Переменной $bar присваивается ссылка на объект $foo поэтому ответ будет 87654321

### 9. Что выведет код и почему?

```php
$i = 10;
$i += ++$i + $i + $i++; 
print $i;
```
12 + (11 + 11 + 11)
 4     1    2   3
Порядок выполнения операций в данном выражении не определен явно. Результат может отличаться в зависимости от конкретной реализации и оптимизации компилятора.

### 10. Найти минимальное расстояние (разность) между произвольными двумя числами из массива (ниже аналоги)

```php
function distClosestNumbers($data) { 
        // try to implement it!
}

$array = [3, 9, 50, 15, 99, 7, 98, 65];
$result = distClosestNumbers($array);
echo $result;
```

Решение в лоб — прямой перебор вложенным массивом, но его сложность — O(n²).
Оптимальное решение — сначала отсортировать массив по возрастанию или убыванию, потом линейно пройтись и найти
минимальное расстояние между двумя соседними числами. В этом случае временная сложность алгоритма — O(n log n).

### 11. Какие есть способы ограничения поступающих запросов на покупку 3 товаров, если хотят купить одновременно 50 пользователей

Ограничение на уровне приложения:

- Очереди (Queues) 
- Блокировки (Locks)

Ограничение на уровне БД:

- Транзакции (Transactions) 
- Хранимые процедуры (Stored Procedures)

Ограничение на уровне приложения и БД:

- Кэширование (Caching)

### 12. Максимизировать свою прибыль, выбрав первый день для покупки одной акции и выбрав другой день в будущем для продажи этой акции

```php
# Вам дан массив цен, где prices[i] — цена акции на i-й день.
# Вы хотите максимизировать свою прибыль, выбрав один день для покупки одной акции и
# выбрав другой день в будущем для продажи этой акции.
# Верните максимальную прибыль, которую вы можете получить от этой сделки.
# Если вы не можете получить никакой прибыли, верните 0.
#
####### Пример 1 #######
# Входящие данные: prices = [7,1,5,3,6,4]
# Вывод: 5
# Обьяснение: Купить на 2-ой день (цена = 1) и продать на 5-ый день (цена = 6), выгода = 6-1 = 5.
# Обратите внимание, что покупка во 2-й день и продажа в 1-й день не разрешены,
# потому что вы должны купить перед продажей.
#
####### Пример 2 #######
# Входящие данные: prices = [7,6,4,3,1]
# Вывод: 0
# Обьяснение: В этом случае транзакции не совершаются, а максимальная прибыль = 0.

// Implementation:

/**
 * @param Integer[] $prices
 * @return Integer
 */
function maxProfit(int ...$prices): int {
    $firstDay = PHP_INT_MAX;
    $indexStart = 0;
    foreach($prices as $index => $price) {
        if ($firstDay > $price ) {
            $firstDay = $price;
            $indexStart = $index;
        }
    }

    if ($firstDay == PHP_INT_MAX) {
        return 0;
    }

    $benefit = 0;
    for ($i = $indexStart + 1; $i < count($prices) - 1; $i++) {
        $diff = $prices[$i] - $firstDay;
        if ($benefit < $diff) {
            $benefit = $diff;
        }
    }

    return $benefit;
}

$testData = [
    [
        [7,1,5,3,6,4],
        5,
    ],
    [
        [7,6,4,3,1],
        0,
    ],
];

foreach ($testData as $i=>$case){
    $expected = $case[1];
    $actual = maxProfit(...$case[0]);
    if($actual != $expected){
        echo sprintf('Case %d failed'.PHP_EOL, $i);
    } else{
        echo sprintf('Case %d succeed'.PHP_EOL, $i);
    }
}
```

### 13. Футбольный тотализатор

```php
/*Тотализатор
Есть футбольный тотализатор. Каждый участник делает ставку на результат матча (счет). После окончания матча происходит проверка: если человек угадал счет, система начисляет ему 2 балла; если человек угадывает только исход матча — 1 балл, и если не угадывает ничего — 0 баллов.
Напишите функцию, которая возвращает словарь (или список) баллов выигранных участниками (юзер1:баллы_юзера1, юзер2:баллы_юзера2, ...). Функция принимает 2 аргумента:
ставки нескольких участников в виде словаря/списка (юзер1:счет1, юзер2:счет2, ...)
результат матча строкой (“3:4”)
*/
const MAX_SCORE = 2;
const MED_SCORE = 1;
const MIN_SCORE = 0;

function calculateScores(array $bets, string $result): array 
{
 [$fistTeamResut, $seciondTeamResult] = explode(':', $result);
 $scoreUserResult = [];
 
 $resultMatch = $fistTeamResut <=> $seciondTeamResult;
 
 foreach ($best as $user => $bet) {
  [$betFistTeam, $betSeciondTeam] =explode(':', $bet);
  
  $betResultMatch = $betFistTeam <=> $betSeciondTeam;
  
  if ($betFistTeam === $fistTeamResut && $betSeciondTeam === $seciondTeamResult) {
   $scoreUserResult[$user] = self::MAX_SCORE;
  } elseif ($betResultMatch === $resultMatch) {
   $scoreUserResult[$user] = self::MED_SCORE;
  } else {
   $scoreUserResult[$user] = self::MIN_SCORE;
  }
 }
}
```

### 14. Сервис знакомств

```php
// Сервис знакомств, регистрация пользователей. После регистрации нужно отправить сообщение 'Privet' через SMS сообщение и на почту.
 
class UserService
{
    public function __construct(){
        
    }
    
    public function register(UserDto $userDto): User {
        // бизнес-логика регистрации
        $user = $this->save($userDto);
        
        $event = new NotifyEvent($userDto);
        $this->dipatcher->dispatch($event);
        
        return $user;
    }
 
    // Логика сохранения пользователя уже реализована и зашита в функции save
    private function save($userDto): User {
    }
}

class NotifyUser {
    
    public function __construct(EmailClient $emailClient, SmsClient $smsClient){
        $this->emailClient = $emailClient;
        $this->smsClient = $smsClient;
    }
    
    public function onSendEmail(NotifyEvent $event) {
        $userDto = $event->getValue();
        
        $this->emailClient->sendEmail($userDto->email, $userDto->message);
    }
    
        
    public function onSendSms(NotifyEvent $event) {
        $userDto = $event->getValue();
        
        $this->smsClient->sendSms($userDto->phone, $userDto->countryCode, $userDto->message);
    }
}
```

### 15. Отправки в очередь различных сообщений

```php
/**
 * Данная структура классов предназначена для отправки в очередь различных сообщений по статусу посылки
 * Какие проблемы могут возникнуть и что можно улучшить в приведенном коде.
 * 
 * Применение принципов SOLID и паттернов - приветствуется. Результат рефакторинга нужно покрыть тестами.
 */ 

declare(strict_types=1);

class Producer
{
    public function send($topic, $key, $body)
    {
        // Инфраструктурны код, производящий отправку сообщения
        // коннект к Kafka, отправка сообщения и т.д.
    }
}

//---------------------------

final class ParcelSender
{
    public function __construct(private Producer $producer, private BodyProcessor $bodyProcessor ){
    }
    
    
     
    public function send(ParcelMessage $parselMessage): void
    {
        // Сборка параметров сообщения из переданных template и data
        //
        $key = $this->data->getId();
        $body = $bodyProcessor->process($template, $data);... // $template + $data
         
        $producer->send($this->topic, $key, $body);
    }
}

enum Template
{
    case CREATED;
    case SENDED;
    case DELIVERED;
}

final class ParcelMessage
{
    protected $topic;

    protected $data;
    
    public function setData(Parcel $data)
    {
        $this->data = $data;
    }
}


//--- вызов в коде
$parcelMessage = new ParcelMessage();
$parcelMessage->setData($entityManager->getRepository('App:Parcel')->find(123));
$parcelMessage->send("parcel.status", "created", "");
```

[Назад](../../../README.md)