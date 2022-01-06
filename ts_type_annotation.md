## 理解Typescript中的类型注释

> 此教程中,你将学会TS中的类型注释

### 什么是TS中的类型注释

TS使用类型注释精确的指定变量,函数,对象等的类型.

TS在指定的标识后使用`:type` 作为类型注释, 这里的`type`可以为任意有效的类型.

一旦标识符被类型注释后,它就只能以指定的类型使用,这时如果此标识被用作不同的类型,TS编译器会抛出错误.

### 变量和常量的类型注释

接下来的语法展示了如何为变量和常量指定类型

```ts
let variableName: type;
let variableName: type = value;
const constantName: type = value;
```

在这个例子中,类型注释是在变量和常量的名字的后面,前置分号(`:`)

接下来用`number` 为一个变量注释

```ts
let counter: number;
```

之后你只能给这个 `counter` 变量给一个数字:

```ts
counter = 1;
```

如果给`counter`赋值一个字符串,你会看到报错:

```ts
let counter: number;
counter = 'Hello'; // 编译报错 
```

错误:

```ts
Type '"Hello"' is not assignable to type 'number'.
```

你可以同时为一个变量注释类型,然后用一个单独的语句初始化,像这样:

```ts
let counter: number = 1;
```

在这个例子中,我们使用`number`注释`counter` ,初始化值为1.

下面是一些基础类型注释的例子:

```ts
let name: string = 'John';
let age: number = 25;
let active: boolean = true;
```

以上例子中: `name`变量获得`string` 类型, `age` 变量获得`number`类型,`active`获得`boolean`类型.

### 类型注释举例

#### 数组

给一个数组类型注释需要使用指定类型跟随一个方括号 `: type[]` 

```ts
let arrayName: type[];
```

 像这样,声明一个字符类型的集合

```ts
let names: string[] = ['John', 'Jane', 'Peter', 'David', 'Mary'];
```

#### 对象

为对象指定一个类型,像这样:

```ts
let person: {
   name: string;
   age: number
};

person = {
   name: 'John',
   age: 25
}; // 有效
```

在这个例子中, `person`对象只接受拥有两个属性的对象: {<ruby>name<rp></rp><rt>string</rt><rp></rp></ruby> , <ruby>age<rp> </rp><rt>number</rt><rp></rp></ruby> } 

#### 函数参数和返回值类型

如下是一个有参数类型和返回值注释的函数声明:

```ts
let greeting : (name: string) => string;
```

可以给这个变量`greeting`赋值任意函数接受一个字符串返回字符串:

```ts
greeting = function (name: string) {
    return `Hi ${name}`;
};
```

而下面的会报错,因为赋值的函数类型不匹配`greeting` 的类型

```ts
greeting = function () {
    console.log('Hello');
};
```

报错:

```ts
Type '() => void' is not assignable to type '(name: string) => string'. Type 'void' is not assignable to type 'string'.
```

### 总结

- 使用`:[type]` 类型注释去准确为一个变量,函数,函数返回值等指定类型.



<div alt="fig">
<a href="https://github.com/Nico-M?tab=repositories" target="_blank" alt="null"><img src="https://img.shields.io/badge/-GitHub-181717?style=flat-square&logo=github"></a>
</div>

