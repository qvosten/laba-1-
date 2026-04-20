# Задача
1. Проверка наличия элемента в массиве
---
1. Реализация

```python
def poisk(x, arr):
    for i in range(len(arr) ):
        if x == arr[i]:
            return True
    return False
```
 2.Функция измерения времени
```python
import time
def measure_time(func, arr, x):
    start = time.perf_counter()
    func(x, arr)
    end = time.perf_counter()
    return end - start
```

3.Функция генерации данных
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


def measure_time(func, arr, x):
    start = time.perf_counter()
    func(x, arr)
    end = time.perf_counter()
    return end - start


def generate_array(n):
    arr = []
    for i in range(n):
        arr.append(random.randint(0, 10000))
    return arr


def poisk(x, arr):
    for i in range(len(arr) ):
        if x == arr[i]:
            return True
    return False

sizes = [100, 1000, 5000, 10_000]
for n in sizes:
    arr = generate_array(n)
    x = random.randint(0, 10000)
    t = measure_time(poisk, arr, x)
    print(n, f"{t:.5f}", poisk(x, arr))
```

| n | t,с |
|---|---|
| 100 | 0.000004 |
| 1000 | 0.000026 |
| 5000 | 0.000147 |
| 10000 | 0.000212 |
