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

###  解构取值

在使用对象的多个属性时，使用对象解构

```js
// bad
function getFullName(user){
  const firstName = user.firstName;
  const lastName = user.lastName;
  return `${firstName}${lastName}`;
}

// good
function getFullName(user){
  const { firstName, lastName } = user;
  return `${firstName}${lastName}`;
}

// best
function getFullName({ firstName, lastName }){
  return `${firstName}${lastName}`;
}
```

数组（元组）解构

```js
// bad
const location = [118, 32];
const longitude= location[0];
const latitude= location[1];

// good
const [longitude, latitude] = location;
```

## 函数

