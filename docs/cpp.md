# Мои успехи в C++

## Задача 1: Название с Codewars
??? success "Посмотреть решение"
    ```cpp
    // Твой код здесь
    ```
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
    **Разбор:** Тут я узнал про `int` и `cout`.

---

