# Задание 3: Бинарный поиск

1. Реализация
```python
def bin_poisk(arr, x):
    left = 0
    right = len(arr) - 1
    while left <= right:
        mid = (left + right) // 2

        if arr[mid] == x:
            return mid

        if arr[mid] < x:
            left = mid + 1
        else:
            right = mid - 1

    return False
```

2. Функция измерения времени
```python
import time
def measure_time(func, arr, x):
    start = time.perf_counter()
    func(arr, x)
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
    return sorted(arr)
```
4. Эксперимент
```python
import time
import random


def bin_poisk(arr, x):
    left = 0
    right = len(arr) - 1
    while left <= right:
        mid = (left + right) // 2

        if arr[mid] == x:
            return mid

        if arr[mid] < x:
            left = mid + 1
        else:
            right = mid - 1

    return False


def generate_array(n):
    arr = []
    for i in range(n):
        arr.append(random.randint(0, 10000))
    return sorted(arr)

def measure_time(func, arr, x):
    start = time.perf_counter()
    func(arr, x)
    end = time.perf_counter()
    return end - start

sizes = [100, 1000, 5000, 10_000]
for n in sizes:
    arr = generate_array(n)
    x = random.randint(0, 10000)
    t = measure_time(bin_poisk, arr, x)
    print(n, f"{t:.10f}", bin_poisk(arr, x))
```
| n | t,с |
|---|---|
| 100 | 0.0000031000|
| 1000 | 0.0000023000 |
| 5000 | 0.0000030000 |
| 10000 |0.0000046000 |
