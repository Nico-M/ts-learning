## TS 数字

> Typescript中的数字类型

在Typescript中所有的数字既可以是浮点值也可以是大整数.浮点数会有`number`类型,而巨型整数的类型为`bigint`.

### 数字类型

如何声明一个浮点类型的变量:

```ts
let price: number;
```

或者你可以直接初始化一个数字变量

```ts
let price = 9.95;
```

和JS一样,TypeScript支持十进制、十六进制、二进制和八进制文本的数字文本.

### 十进制

下面是一些十进制的数字:

```ts
let counter: number = 0;
let x: number = 100, 
    y: number = 200;
```

### 二进制

二进制的数字以0开头,跟着小写或大写的'B', `0b` 或者`0B`:

```TS
let bin = 0b100;
let anotherBin: number = 0B010;
```

注意: `0b` 或者`0B`后面的数字必须是`0`或者`1`.

### 八进制

八进制的数字以0开头,接着字母o(ES2015)`0o`. 后面的数字需在`0~7` 之间:

```ts
let octal: number = 0o10;
```

### 十六进制

十六进制数字以0开头，后跟小写或大写字母X（`0x`或 `0X`）。`0x` 之后的数字必须在（0123456789ABCDEF）在范围内。例如：

```ts
let hexadecimal: number = 0XA;
```

JavaScript有`Number`类型（大写字母N），指的是非原始对象。你应该在TypeScript中尽量少地使用此数字类型。

### 大整数

大整数指的是数字大于2^53^ – 1,大整数的字面以`n`字符结尾:

```ts
let big: bigint = 9007199254740991n;
```

### 总结

- 在Typescript中所有的数字既可以是浮点值也可以是大整数
- 尽量少地使用`Number`数字类型。





---



<p alt="center"><a alt="null" href="./index"><span alt="mt-icon">home</span></a> <p>


<div alt="fig">
<a href="https://github.com/Nico-M?tab=repositories" target="_blank" alt="null"><img src="https://img.shields.io/badge/-GitHub-181717?style=flat-square&logo=github"></a>
</div>

