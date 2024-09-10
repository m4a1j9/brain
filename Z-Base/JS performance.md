2024.09.10 11:28
Tags: #1quest 

# JS performance

### Создание копии массива
```js
// Гораздо раз быстрее
arr.slice();

// чем это
[...arr]
```
При копировании массива длинной 1, быстрее в 7 раз.
При копировании массива длинной 10 000, быстрее в 120 раз.

Код для тестирования:
```js
const arr = Array.from({ length: 10000 }, (_, i) => ({x: i, y: i}));
console.time();
for (let i = 0; i < 100000; i++) {
  //const newArr = [...arr];
  const newArr = arr.slice();
}
console.timeEnd();
```

### Деструктуризация

```js
// Гораздо раз быстрее
const { 0: a, 1: b, 2: c, 3: d } = arr;

const [a, b, c, d] = arr;
[...arr]
```
При деструктуризации массива длинной 1, быстрее в 2.5 раз.
При деструктуризации массива длинной 4, быстрее в 3.5 раз.

Код для тестирования:
```js
const arr = [0, 1, 2, 3];
console.time();
for (let i = 0; i < 100000000; i++) {
  //const [a, b, c, d] = arr;
  const { 0: a, 1: b, 2: c, 3: d } = arr;
}
console.timeEnd();
```


### Zero-Links
- [[00 JS]]
- [[00 Тестирование]]
- [[00 Tips]]

### Links
- 