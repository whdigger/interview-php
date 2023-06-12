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
[1, 7, 3] 4 должно вывести [0, 2]

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

- Посмотрю на вывод SHOW PROCESSLIST; в консоли MySQL на кол-во и время выполнения запросов..
- Хорошо. Допустим, там постоянно висит 2-3 различных запроса с большим временем выполнения. Ваши действия?
- Оптимизация базы, индексы, объединения.
- Ок, а если много различных запросов с небольшим временем выполнения?
- Необходимо использовать кэширование запросов
- Ок, допилили кэширование, но проблема все же осталась
- Некорректная работа кэширующего механизма?
- Допустим. Давайте немного скорректируем условия - вы открываете консоль MySQL и видите там обычное кол-во запросов. В чем ещё может быть проблема?
- Долгие запросы к сторонним ресурсам

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

```
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
минимальное расстояние между двумя соседними числами. В этом случае временнáя сложность алгоритма — O(n log n).