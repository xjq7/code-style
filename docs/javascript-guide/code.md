# 代码

## 对象

### 使用扩展运算符代替 Object.assign 浅拷贝对象

```js
// very bad
const original = { a: 1, b: 2 };
const copy = Object.assign(original, { c: 3 }); // 影响了原对象
delete copy.a; // 还原了原对象

// bad
const original = { a: 1, b: 2 };
const copy = Object.assign({}, original, { c: 3 }); // copy => { a: 1, b: 2, c: 3 }

// good
const original = { a: 1, b: 2 };
const copy = { ...original, c: 3 }; // copy => { a: 1, b: 2, c: 3 }

const { a, ...noA } = copy; // noA => { b: 2, c: 3 }
```
