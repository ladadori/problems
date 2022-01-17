В данном упражнении необходимо реализовать стековую машину, то есть алгоритм, проводящий вычисления по обратной польской записи.

Обратная польская нотация или постфиксная нотация — форма записи математических и логических выражений, в которой операнды расположены перед знаками операций. Выражение читается слева направо. Когда в выражении встречается знак операции, выполняется соответствующая операция над двумя ближайшими операндами, находящимися слева от знака операции. Результат операции заменяет в выражении последовательность её операндов и знак, после чего выражение вычисляется дальше по тому же правилу. Таким образом, результатом вычисления всего выражения становится результат последней вычисленной операции.

Например, выражение `(1 + 2) * 4 + 3` в постфиксной нотации будет выглядеть так: `1 2 + 4 * 3 +`, а результат вычисления: `15`. Другой пример - выражение: `7 - 2 * 3`, в постфиксной нотации: `7 2 3 * -`, результат: `1`.

### Задача
Экспортируйте по умолчанию функцию, которая принимает массив, каждый элемент которого содержит число или знак операции (+, -, *, /). Функция должна вернуть результат вычисления по обратной польской записи. Если в какой-то момент происходит деление на ноль, функция должна вернуть значение `null`.

### Пример

```
calcInPolishNotation([1, 2, '+', 4, '*', 3, '+']); // 15
calcInPolishNotation([7, 2, 3, '*', '-']); // 1
```

### Решение учителя

```
const calcInPolishNotation = (array) => {
  const stack = [];
  const operators = ['*', '/', '+', '-'];

  for (const value of array) {
    if (!operators.includes(value)) {
      stack.push(value);
      continue;
    }

    const b = stack.pop();
    const a = stack.pop();
    let result;

    switch (value) {
      case '*':
        result = a * b;
        break;
      case '/':
        result = b === 0 ? null : a / b;
        break;
      case '+':
        result = a + b;
        break;
      case '-':
        result = a - b;
        break;
      default:
        break;
    }

    if (result === null) {
      return result;
    }

    stack.push(result);
  }

  return stack.pop();
};

export default calcInPolishNotation;
```