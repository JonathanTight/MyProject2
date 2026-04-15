# Мои успехи в C++

## Задача 1: [Codewars: "Two Sum"](https://www.codewars.com/kata/52c31f8e6605bcc646000082/train/cpp) <small>(*[Based on Leetcode](https://leetcode.com/problems/two-sum/)*)</small>

Write a function that takes an array of numbers (integers for the tests) and a target number. It should find two different items in the array that, when added together, give the target value. The indexes of these items should then be returned in a tuple / list (depending on your language) like so: (index1, index2).

For the purposes of this kata, some tests may have multiple answers; any valid solutions will be accepted.

The input will always be valid (numbers will be an array of length 2 or greater, and all of the items will be numbers; target will always be the sum of two different items from that array).

<small>**Примечание: Хотя в задаче просят "tuple", в C++ для пары значений лучше всего подходит `std::pair`.**</small>

???+ "На русском:" 
    Напишите функцию, которая принимает массив чисел (целых чисел для тестов) и целевое число (`target`). Она должна найти в массиве два разных элемента, которые при сложении дают целевое значение. Индексы этих элементов должны быть возвращены в виде пары (tuple/list) вот так: `(index1, index2)`.

    В рамках этого ката некоторые тесты могут иметь несколько вариантов ответа; любой правильный ответ будет принят.
    
    Входные данные всегда корректны: массив длиной 2 или более, все элементы — числа; `target` всегда является суммой двух разных элементов из этого массива.



```cpp
Примеры данных:

two_sum({1, 2, 3}, 4); // returns {0, 2} or {2, 0}
two_sum({3, 2, 4}, 6); // returns {1, 2} or {2, 1}
```
???+ "Решение:"
    ```cpp
    #include <vector>

    std::pair<std::size_t, std::size_t> two_sum(const std::vector<int>& numbers, int target) {
        for (std::size_t i = 0; i < numbers.size(); ++i) {
            for (std::size_t j = i + 1; j < numbers.size(); ++j) {
                if (numbers[i] + numbers[j] == target) {
                    return {i, j};
                }
            }
        }
        return {0, 0};
    }
    ```
<small>`#include <vector>` — это подключение стандартной библиотеки для работы с динамическими массивами (векторами).  
Зачем: Без этой строки компилятор не поймет, что такое std::vector, и выдаст ошибку.  
Почему на Codewars его нет: На Codewars этот заголовок (и другие базовые) часто уже скрыто подключен за кулисами в тестовой среде для удобства, чтобы ты писал только саму функцию.
В реальном проекте в VS Code его обязательно нужно писать самому в начале файла.
</small>
>## Инсайт дня: Индексы vs Размер (Off-by-one error)

**Индекс (Index)** — это смещение (дистанция) от начала. От первого элемента до него самого — 0 шагов. Поэтому первый элемент имеет индекс `0`.  
**Размер (Size)** — это общее количество штук. Если в массиве есть хотя бы один предмет, его размер — `1`.  
<small>В векторе размером `N` последний доступный индекс всегда равен `N - 1`. </small>  

**Пример из кода:**  
    Если `numbers.size() == 5`, то:  
Элементы: `1-й`, `2-й`, `3-й`, `4-й`, `5-й`.  
Индексы: `0`, `1`, `2`, `3`, `4`.  
Попытка обратиться к `numbers[5]` приведет к ошибке, так как индекса `5` не существует.

> **Вывод:** Всегда помнить, что цикл должен идти до `i < size`, а не `i <= size`.
