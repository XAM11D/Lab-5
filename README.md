# Lab-5
Лабораторна робота 5: Робота з функціями та структурами даних у Python

Мета роботи
Мета цієї лабораторної роботи - навчитися працювати з різними структурами даних у Python, такими як словники, масиви та списки. Завдання включають об'єднання словників, інтерпретацію рядків як масивів, обробку списків, роботу з унікальними елементами та комбінаторикою. Очікувані результати включають написання та тестування функцій, що виконують ці завдання.

Опис завдання
Завдання 1: Об'єднання списку словників в один.
Завдання 2: Інтерпретація рядка як масиву, отримання його байтового представлення.
Завдання 3: Отримання унікальних елементів із масиву.
Завдання 4: Пошук відсутнього числа в діапазоні 10-20 у списку.
Завдання 5: Отримання унікальних значень зі списку словників.
Завдання 6: Підрахунок кількості можливих комбінацій із ключів у списку словників.
Завдання 7: Знаходження трьох найбільших ключів у словнику.
Завдання 8: Об'єднання значень за однаковими ключами зі списку словників.

Виконання роботи

Завдання 1:
def task1(dict_list):
    merged_dict = {}
    for dictionary in dict_list:
        merged_dict.update(dictionary)
    return merged_dict

# Приклад використання:
dict_list = [{'a': 1}, {'b': 2}, {'c': 3}]
print(task1(dict_list))  # Виведе: {'a': 1, 'b': 2, 'c': 3}

Завдання 2:
import array
import binascii

def task2(input_string):
    array_name, values_string = input_string.split(':')
    array_type = values_string.split(',')[0].split('(')[1]
    values = [int(val.strip()) for val in values_string.split('[')[1].split(']')[0].split(',') if val.strip()]
    interpreted_array = array.array(array_type, values)
    bytes_representation = interpreted_array.tobytes()
    return interpreted_array, bytes_representation

# Приклад використання:
input_string = "arr:array('i', [1, 2, 3, 4, 5])"
interpreted_array, bytes_representation = task2(input_string)
print(interpreted_array)  # Виведе: array('i', [1, 2, 3, 4, 5])
print(binascii.hexlify(bytes_representation))  # Виведе байтове представлення

Завдання 3:
def task3(input_array):
    unique_elements = []
    for item in input_array:
        if item not in unique_elements:
            unique_elements.append(item)
    return unique_elements

# Приклад використання:
input_array = [1, 2, 2, 3, 4, 4, 5]
print(task3(input_array))  # Виведе: [1, 2, 3, 4, 5]

Завдання 4:
def task4(input_array):
    full_range = set(range(10, 21))
    input_set = set(input_array)
    missing_numbers = full_range - input_set

    if missing_numbers:
        return missing_numbers.pop()
    else:
        return None

# Приклад використання:
input_array = [10, 11, 12, 14, 15, 16, 17, 18, 19, 20]
print(task4(input_array))  # Виведе: 13 (наприклад)

Завдання 5:
def task5(dict_list):
    distinct = []
    for dictionary in dict_list:
        for value in dictionary.values():
            if value not in distinct:
                distinct.append(value)
    unique_count = len(distinct)
    return distinct

# Приклад використання:
dict_list = [{'a': 1}, {'b': 2}, {'c': 3}, {'a': 1}]
print(task5(dict_list))  # Виведе: [1, 2, 3]

Завдання 6:
def task6(dictionaries):
    letters_lists = [list(dictionary.keys()) for dictionary in dictionaries]
    combinations_count = 1
    for letters_list in letters_lists:
        combinations_count *= len(letters_list)
    return combinations_count

# Приклад використання:
dictionaries = [{'a': 1, 'b': 2}, {'c': 3, 'd': 4}]
print(task6(dictionaries))  # Виведе: 

Завдання 7:
def task7(dictionary):
    sorted_keys = sorted(dictionary.keys(), reverse=True)
    largest_keys = sorted_keys[:3]
    return largest_keys

# Приклад використання:
dictionary = {'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5}
print(task7(dictionary))  # Виведе: ['e', 'd', 'c']

Завдання 8:
def task8(dict_list):
    combined_values = {}
    for dictionary in dict_list:
        item = dictionary['item']
        amount = dictionary['amount']
        if item in combined_values:
            combined_values[item] += amount
        else:
            combined_values[item] = amount
    return combined_values

# Приклад використання:
dict_list = [{'item': 'apple', 'amount': 5}, {'item': 'banana', 'amount': 3}, {'item': 'apple', 'amount': 2}]
print(task8(dict_list))  # Виведе: {'apple': 7, 'banana': 3}

Приклади виводу програми:
Завдання 1: {'a': 1, 'b': 2, 'c': 3}
Завдання 2: array('i', [1, 2, 3, 4, 5]) та байтове представлення
Завдання 3: [1, 2, 3, 4, 5]
Завдання 4: 13 (наприклад)
Завдання 5: [1, 2, 3]
Завдання 6: 4
Завдання 7: ['e', 'd', 'c']
Завдання 8: {'apple': 7, 'banana': 3}

Вимоги до середовища:Python 3.x
