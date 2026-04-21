# Задание 5: Провести замеры алгоритмической и пространственной сложности любой из сортировок

Сортировка выбором(selection sort)
1. Реализация
```python
def selection_sort(arr):
    for i in range(len(arr)):
        index_min = i
        for j in range(i + 1 , len(arr)):
            if arr[j] < arr[index_min]:
                index_min = j
        x = arr[i]
        arr[i] = arr[index_min]
        arr[index_min] = x
    return arr
```

2. Функция измерения времени
```python
import time
def measure_time(func, data):
    start = time.perf_counter()
    func(data)
    end = time.perf_counter()
    return end - start
```
3. Функция генерации данных
```python
import random
def measure_memory(func, data):
    tracemalloc.start()
    func(data)
    current, peak = tracemalloc.get_traced_memory()
    tracemalloc.stop()
    return peak
```

4.Функция замера пространственной сложности
```python
import tracemalloc
def measure_memory(func, data):
    tracemalloc.start()
    func(data)
    current, peak = tracemalloc.get_traced_memory()
    tracemalloc.stop()
    return peak
```
4. Эксперимент
```python
import time
import random
import tracemallocdef selection_sort(arr):
    for i in range(len(arr)):
        index_min = i
        for j in range(i + 1 , len(arr)):
            if arr[j] < arr[index_min]:
                index_min = j
        x = arr[i]
        arr[i] = arr[index_min]
        arr[index_min] = x
    return arr



def generate_array(n):
    arr = []
    for i in range(n):
        arr.append(random.randint(0, 10000))
    return arr

def measure_time(func, data):
    start = time.perf_counter()
    func(data)
    end = time.perf_counter()
    return end - start

def measure_memory(func, data):
    tracemalloc.start()
    func(data)
    current, peak = tracemalloc.get_traced_memory()
    tracemalloc.stop()
    return peak

sizes = [100, 1000, 5000, 1_0000]

for n in sizes:
    arr = generate_array(n)
    t = measure_time(selection_sort, arr)
    m = measure_memory(selection_sort, arr)
    print(n, f"{t:.7f}", m)
```
| n      | t       | m      |
|--------|---------|--------|
| 100    | 0.0001428 | 112   |
| 1000   | 0.0159688 | 268   |
| 5000   | 0.86854 | 268   |
| 10000  | 5.23819 | 268  |

