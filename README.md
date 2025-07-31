# Задачи по C++ для практики

**Рекомендация:** Лучше всего решать задачи в онлайн-компиляторе: [OnlineGDB C++ Compiler](https://www.onlinegdb.com/online_c++_compiler)

---

## Простые конструкции

### Задача 1: Сумма двух чисел
**Описание:** Напишите программу, которая запрашивает два целых числа и выводит их сумму.  
**Пример ввода:**  
```
5
7
```
**Пример вывода:**  
```
12
```
<details>
<summary>Решение</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    cin >> a >> b;
    cout << a + b;
    return 0;
}
```
</details>

---

### Задача 2: Конвертер валют
**Описание:** Переведите доллары в рубли (курс: 1 доллар = 90.5 рублей).  
**Пример ввода:**  
```
10
```
**Пример вывода:**  
```
905
```
<details>
<summary>Решение</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    double dollars;
    cin >> dollars;
    cout << dollars * 90.5;
    return 0;
}
```
</details>

---

## Циклы

### Задача 3: Сумма четных чисел
**Описание:** Выведите сумму всех четных чисел от 1 до N (включительно).  
**Пример ввода:**  
```
5
```
**Пример вывода:**  
```
6  // (2 + 4)
```
<details>
<summary>Решение</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, sum = 0;
    cin >> n;
    for(int i = 1; i <= n; i++) {
        if(i % 2 == 0) {
            sum += i;
        }
    }
    cout << sum;
    return 0;
}
```
</details>

---

### Задача 4: Факториал
**Описание:** Вычислите факториал числа N (N! = 1*2*3*...*N).  
**Пример ввода:**  
```
5
```
**Пример вывода:**  
```
120
```
<details>
<summary>Решение</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    long factorial = 1;
    cin >> n;
    
    for(int i = 1; i <= n; i++) {
        factorial *= i;
    }
    cout << factorial;
    return 0;
}
```
</details>

---

## Циклы с break/continue и условия

### Задача 5: Простые числа
**Описание:** Определите, является ли число простым (делится только на 1 и на себя).  
**Пример ввода:**  
```
7
```
**Пример вывода:**  
```
Prime
```
<details>
<summary>Решение</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    bool isPrime = true;
    
    if(n <= 1) isPrime = false;
    for(int i = 2; i*i <= n; i++) {
        if(n % i == 0) {
            isPrime = false;
            break;
        }
    }
    
    cout << (isPrime ? "Prime" : "Not prime");
    return 0;
}
```
</details>

---

### Задача 6: Пропуск отрицательных
**Описание:** Суммируйте положительные числа до первого отрицательного.  
**Пример ввода:**  
```
3 5 -2 4
```
**Пример вывода:**  
```
8
```
<details>
<summary>Решение</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    int num, sum = 0;
    while(cin >> num) {
        if(num < 0) break;
        sum += num;
    }
    cout << sum;
    return 0;
}
```
</details>

---

### Задача 7: Кратные тройки
**Описание:** Выведите числа от 1 до 50, пропуская числа, кратные 3.  
**Пример вывода:**  
```
1 2 4 5 7 ... 49 50
```
<details>
<summary>Решение</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    for(int i = 1; i <= 50; i++) {
        if(i % 3 == 0) continue;
        cout << i << " ";
    }
    return 0;
}
```
</details>

---

### Задача 8: Минимум и максимум
**Описание:** Найдите минимальное и максимальное число в последовательности (конец ввода - 0).  
**Пример ввода:**  
```
5 2 9 1 0
```
**Пример вывода:**  
```
Min: 1
Max: 9
```
<details>
<summary>Решение</summary>

```cpp
#include <iostream>
#include <climits>
using namespace std;

int main() {
    int num, min = INT_MAX, max = INT_MIN;
    while(cin >> num && num != 0) {
        if(num < min) min = num;
        if(num > max) max = num;
    }
    cout << "Min: " << min << "\nMax: " << max;
    return 0;
}
```
</details>

---

### Задача 9: Сумма цифр
**Описание:** Выведите сумму цифр числа (для отрицательных игнорируйте знак).  
**Пример ввода:**  
```
-123
```
**Пример вывода:**  
```
6
```
<details>
<summary>Решение</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, sum = 0;
    cin >> n;
    if(n < 0) n = -n;
    
    while(n > 0) {
        sum += n % 10;
        n /= 10;
    }
    cout << sum;
    return 0;
}
```
</details>

---

### Задача 10: Калькулятор
**Описание:** Калькулятор с операциями +, -, *, / (завершается при вводе 'q').  
**Пример ввода:**  
```
5 + 3
10 / 2
q
```
**Пример вывода:**  
```
8
5
```
<details>
<summary>Решение</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    char op;
    double a, b;
    
    while(cin >> a >> op) {
        if(op == 'q') break;
        cin >> b;
        
        switch(op) {
            case '+': cout << a + b; break;
            case '-': cout << a - b; break;
            case '*': cout << a * b; break;
            case '/': 
                if(b == 0) cout << "Error!";
                else cout << a / b;
                break;
            default: cout << "Invalid operator";
        }
        cout << endl;
    }
    return 0;
}
```
</details>

---

## Указатели

### Задача 11: Обмен значений
**Описание:** Поменяйте значения двух переменных через указатели.  
**Пример ввода:**  
```
10 20
```
**Пример вывода:**  
```
20 10
```
<details>
<summary>Решение</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    cin >> a >> b;
    
    int *ptrA = &a, *ptrB = &b;
    int temp = *ptrA;
    *ptrA = *ptrB;
    *ptrB = temp;
    
    cout << a << " " << b;
    return 0;
}
```
</details>

---

### Задача 12: Сумма через указатели
**Описание:** Вычислите сумму двух чисел, используя указатели.  
**Пример ввода:**  
```
25 75
```
**Пример вывода:**  
```
100
```
<details>
<summary>Решение</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    cin >> a >> b;
    
    int *ptrA = &a, *ptrB = &b;
    cout << *ptrA + *ptrB;
    
    return 0;
}
```
</details>
