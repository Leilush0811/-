from random import randint


# Функция пузырьковой сортировки
def bubble_sort(input_array):
    compare_count = 0
    swap_count = 0
    array = input_array.copy()
    n = len(array)

    for i in range(n - 1):
        for j in range(n - i - 1):
            compare_count += 1
            if array[j] > array[j + 1]:
                swap_count += 1
                array[j], array[j + 1] = array[j + 1], array[j]

    return array, compare_count, swap_count


# Функция сортировки отбором
def selection_sort(input_array):
    compare_count = 0
    swap_count = 0
    array = input_array.copy()
    n = len(array)

    for i in range(n - 1):
        min_index = i
        for j in range(i + 1, n):
            compare_count += 1
            if array[j] < array[min_index]:
                min_index = j
        swap_count += 1
        array[i], array[min_index] = array[min_index], array[i]

    return array, compare_count, swap_count


# Функция создания массива заданного размера из случайных элементов
def generate_array(size):
    array = []
    for i in range(0, size):
        array.append(randint(-1000, 1000))
    return array


# Выполняемый код
sizes = [26, 52, 104, 208, 416, 832, 1664]
for size in sizes:
    array = generate_array(size)
    print(f"---\n"
          f"Размер массива: {size}\n"
          f"Входные значения: {array}\n")
    sorted_array, compare_count, swap_count = bubble_sort(array)
    print(f"Пузырьковая сортировка\n"
          f"Сортированный массив: {sorted_array}\n"
          f"Количество сравнений: {compare_count}\n"
          f"Количество перестановок: {swap_count}\n\n")
    sorted_array, compare_count, swap_count = selection_sort(array)
    print(f"Сортировка отбором\n"
          f"Сортированный массив: {sorted_array}\n"
          f"Количество сравнений: {compare_count}\n"
          f"Количество перестановок: {swap_count}\n"
          f"---\n")
input("Для продолжения нажмите клавишу Enter")

