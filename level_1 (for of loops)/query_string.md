Query String (строка запроса) - часть адреса страницы в интернете, содержащая константы и их значения. Она начинается после вопросительного знака и идет до конца адреса. Пример:

```
# query string: page=5
https://ru.hexlet.io/blog?page=5
Если параметров несколько, то они отделяются амперсандом &:
# query string: page=5&per=10
https://ru.hexlet.io/blog?per=10&page=5
```


### Задание

Реализуйте и экспортируйте функцию по умолчанию, которая принимает на вход список параметров и возвращает сформированный query string из этих параметров:

```JavaScript
import bqs from '../buildQueryString.js';
 
bqs({ per: 10, page: 1 });
// page=1&per=10
bqs({ param: 'all', param1: true });
// param=all&param1=true
```

Имена параметров в выходной строке должны располагаться в алфавитном порядке (то есть их нужно отсортировать).

### Решение учителя

```JavaScript
export default (params) => {
  const keys = Object.keys(params).sort();
  const result = [];

  for (const key of keys) {
    result.push(`${key}=${params[key]}`);
  }

  return result.join('&');
};
```

