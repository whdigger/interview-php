## 1. Как можно реализовать устранение коллизий при хэширование?

- Использовать открытую адресацию (т.е использовать любой свободный слот в хэшмапе)
- Использовать бакеты внутри которых есть односвязные списки

## 2. Какие есть способы реализации очередей?

- Использование циклического массива с возможностью расширения при достижение конца
- Двухсвязные списки с использованием двух стеков, в один пишем, из другого читаем (с переворотом стека)

## 3. Какие способы сортировки для чего лучше применять?

- Сортировка выбором: подходит для сортировки по сети (когда изменить значение очень долго, получить можно быстро), сделать список операций тем кто работает на складе чтобы они сделали перестановку. Используется там где нужно меньшее количество обменов и записи
- Сортировка вставками: не использует доп памяти, устойчивая сортировка