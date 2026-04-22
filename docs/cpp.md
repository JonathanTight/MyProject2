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

???+ "На заметку:"
    <small>`#include <vector>` — это подключение стандартной библиотеки для работы с динамическими массивами (векторами).  
    Зачем: Без этой строки компилятор не поймет, что такое std::vector, и выдаст ошибку.  
    Почему на Codewars его нет: На Codewars этот заголовок (и другие базовые) часто уже скрыто подключен за кулисами в тестовой среде для удобства, чтобы ты писал только саму функцию.
    В реальном проекте в VS Code его обязательно нужно писать самому в начале файла.</small>

<br>
> <big>Инсайт дня: Индексы vs Размер (Off-by-one error)</big>

**Индекс (Index)** — это смещение (дистанция) от начала. От первого элемента до него самого — 0 шагов. Поэтому первый элемент имеет индекс `0`.  
**Размер (Size)** — это общее количество штук. Если в массиве есть хотя бы один предмет, его размер — `1`.  
<small>В векторе размером `N` последний доступный индекс всегда равен `N - 1`. </small>  

**Пример:**  
    Если `numbers.size() == 5`, то:  
Элементы: `1-й`, `2-й`, `3-й`, `4-й`, `5-й`.  
Индексы: `0`, `1`, `2`, `3`, `4`.  
Попытка обратиться к `numbers[5]` приведет к ошибке, так как индекса `5` не существует.

> **Вывод:** Всегда помнить, что цикл должен идти до `i < size`, а не `i <= size`.

---  

---  

---  

---  

---  

## Задача 2: [Codewars: "Even or Odd"](https://codewars.com)

Create a function that takes an integer as an argument and returns "Even" for even numbers or "Odd" for odd numbers.


???+ "На русском:" 
    Создайте функцию, которая принимает целое число в качестве аргумента и возвращает "Even" (Четное) для четных чисел или "Odd" (Нечетное) для нечетных.

```cpp
Примеры данных:

even_or_odd(2);    // returns "Even"
even_or_odd(7);    // returns "Odd"
even_or_odd(-42);  // returns "Even"
```

???+ "Решение:"
    ```cpp
    #include <string>

    std::string even_or_odd(int number) 
    {
      if (number % 2 == 0) {
        return "Even";
      } else {
        return "Odd";
      }
    }
    ```

???+ "На заметку:"
    <small>`std::string` — это тип возвращаемого значения функции, так как мы возвращаем слова, а не числа.  
    Синтаксис `if/else`: условие всегда пишется в круглых скобках `()`, а блоки кода — в фигурных `{}`. Каждая команда внутри заканчивается точкой с запятой `;`.</small>

<br>
> <big>Инсайт дня: Оператор остатка от деления (%)</big>

**Оператор `%` (modulo)** возвращает то, что осталось после деления одного целого числа на другое.  
Если `число % 2 == 0`, значит оно делится на два нацело — это главный способ определить **четность** в программировании.

**Пример:**  
    Если `number == 7`, то `7 % 2` даст `1`. Результат не 0, значит число **нечетное**.  
    Если `number == 8`, то `8 % 2` даст `0`. Результат 0, значит число **четное**.

> **Вывод:** Любая задача, где нужно проверить кратность одного числа другому, решается через оператор `%`.

---

---

---

---

---



## Задача 3: [Codewars: "Convert a Number to a String!"](https://codewars.com)

We need a function that can transform a number (integer) into a string. What ways of achieving this do you know?


???+ "На русском:" 
    Нам нужна функция, которая может преобразовать число (целое число) в строку. Какие способы решения этой задачи вы знаете?

    ```cpp
    Примеры данных:

    123  --> "123"
    999  --> "999"
    -100 --> "-100"
    ```

???+ "Решение:"
    ```cpp
    #include <string>

    std::string number_to_string(int num) {
      return std::to_string(num);
    }
    ```

???+ "На заметку:"
    <small>`#include <string>` — необходимо подключить, чтобы использовать функцию `std::to_string()`.  
    `std::to_string()` — принимает числовые типы (int, float, double) и возвращает их строковое представление (`std::string`). Это самый простой и современный способ конвертации в C++.</small>

<br>
> <big>Инсайт дня: Строка vs Число (Типизация)</big>

**Число (`int`)** — это значение, с которым можно проводить математические операции (сложение, умножение).  
**Строка (`string`)** — это набор символов (текст). Даже если в строке написано `"123"`, компьютер воспринимает это как последовательность символов, а не как число.

**Пример:**  
    Если `num = 123`, то `123 + 1` даст результат `124`.  
    Если мы работаем со строкой `"123"`, то попытка прибавить к ней `"1"` приведет к склейке текста — `"1231"`.

> **Вывод:** Всегда следи за типами данных: для расчетов используй `int`, для вывода текста или хранения строковых ID — `string`.
