### 解构

#### [强制] 不要使用3层及以上的解构。

解释：

过多层次的解构会让代码变得难以阅读。

示例：

```javascript
// bad
let {documentElement: {firstElementChild: {nextSibling}}} = window;
```

#### [建议] 使用解构减少中间变量。

解释：

常见场景如变量值交换，可能产生中间变量。这种场景推荐使用解构。

示例：

```javascript
// good
[x, y] = [y, x];

// bad
let temp = x;
x = y;
y = temp;
```

#### [强制] 仅定义一个变量时不允许使用解构。

解释：

在这种场景下，使用解构将降低代码可读性。

示例：

```javascript
// good
let len = myString.length;

// bad
let {length: len} = myString;
```

#### [强制] 如果不节省编写时产生的中间变量，解构表达式 `=` 号右边不允许是 `ObjectLiteral` 和 `ArrayLiteral`。

解释：

在这种场景下，使用解构将降低代码可读性，通常也并无收益。

示例：

```javascript
// good
let {first: firstName, last: lastName} = person;
let one = 1;
let two = 2;

// bad
let [one, two] = [1, 2];
```

#### [强制] 使用剩余运算符时，剩余运算符之前的所有元素必需具名。

解释：

剩余运算符之前的元素省略名称可能带来较大的程序阅读障碍。如果仅仅为了取数组后几项，请使用 `slice` 方法。

示例：

```javascript
// good
let [one, two, ...anyOther] = myArray;
let other = myArray.slice(3);

// bad
let [,,, ...other] = myArray;
```
