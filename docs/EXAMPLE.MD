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
```

```php
1 << 3
```

### 3. Что выведет программа

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

