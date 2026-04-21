# Задача 2: Поиск второго максимального элемента

1. Реализация

```python
def two_max(arr):
    max_1 = arr[0]
    max_2 = arr[0]
    for x in arr:
        if x > max_1:
            max_2 = max_1
            max_1 = x
        elif x < max_1 and (x > max_2 or max_1 == max_2):
            max_2 = x
    return max_2

```
2. Функция измерения времени
```python
import time
def measure_time(func, arr):
    start = time.perf_counter()
    func(arr)
    end = time.perf_counter()
    return end - start
```
3. Функция генерации данных
```python
import random
def generate_array(n):
    arr = []
    for i in range(n):
        arr.append(random.randint(0, 10000))
    return arr
```
4. Эксперимент
```python
import time
import random


def two_max(arr):
    max_1 = arr[0]
    max_2 = arr[0]
    for x in arr:
        if x > max_1:
            max_2 = max_1
            max_1 = x
        elif x < max_1 and (x > max_2 or max_1 == max_2):
            max_2 = x
    return max_2


def generate_array(n):
    arr = []
    for i in range(n):
        arr.append(random.randint(0, 10000))
    return arr

def measure_time(func, arr):
    start = time.perf_counter()
    func(arr)
    end = time.perf_counter()
    return end - start

sizes = [100, 1000, 5000, 10_000]
for n in sizes:
    arr = generate_array(n)
    t = measure_time(two_max, arr)
    print(n, f"{t:.7f}")
```

 n | t,с |
|---|---|
| 100 | 0.0000057 |
| 1000 | 0.0000439 |
| 5000 | 0.0002046|
| 10000 | 0.0004090 |
