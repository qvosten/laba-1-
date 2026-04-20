# Задание 4: Построение таблицы умножения
1. Реализация
```python
def table(n):
    table = []
    for i in range(1, n + 1):
        row = []
        for j in range(1, n + 1):
            row.append(i * j)
        table.append(row)
    return table
```
2. Функция измерения времени
```python
import time
def measure_time(func, n):
    start = time.perf_counter()
    func(n)
    end = time.perf_counter()
    return end - start
```
3. Эксперимент
```python
import time
import random
def table(n):
    table = []
    for i in range(1, n + 1):
        row = []
        for j in range(1, n + 1):
            row.append(i * j)
        table.append(row)
    return table

def measure_time(func, n):
    start = time.perf_counter()
    func(n)
    end = time.perf_counter()
    return end - start

sizes = [100, 1000, 5000, 10_000]

for n in sizes:
    t = measure_time(table, n)
    print(n, f"{t:.7f}")
```
| n | t,с |
|---|---|
| 100 | 0.0004766 |
| 1000 | 0.0559378 |
| 5000 | 1.4599755 |
| 10000 | 8.2021088 |
