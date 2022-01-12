## 类型推断

类型推断说的是当你没有注释Typescript的类型时,它是如何推断出类型.

### 基本类型推断

当你声明一个变量是,你可以使用类型注释去准确的为它指定一个类型.

```ts
let counter: number;
```

然而,如果你直接初始化这个`number`的变量`counter`, Typescript 会自己推断出这个`counter`的类型是`number`.

```ts
let counter = 0;
```

就相当于这样:

```ts
let counter: number = 0;
```

同样的,当你给一个函数参数赋值时,Typescript会推断默认参数值得类型

```ts
function setCounter(max=100) {
    // ...
}
```

上面, Typescript推导出参数`max`的类型为 `number`

类似,Typescript推导出`increment()` 的返回值类型为`number`

```tsx
function increment(counter: number) {
    return counter++;
}
```

等同于:

```tsx
function increment(counter: number) : number {
    return counter++;
}
```

### 最佳通用的类型算法

试想一下如下的赋值:

```tsx
let items = [1, 2, 3, null];
```

为了推断出`items` 的类型, Typescript需要考虑到数组中的每一个元素类型.

‎它使用最佳的通用类型算法来分析每个候选类型，并选择与所有其他候选类型兼容的类型。‎

在这个例子中, Typescript会选择数字数组(`number[]`)作为最通用类型.

如果在这个数组中增加一个`string` 的子项,Typescript会以 `(number|string)[]` 的类型作为这个数组的推导

```tsx
let items = [0, 1, null, 'Hi'];
```

当Typescript找不到最通用类型时,将会采用联合类型,

```tsx
let arr = [new Date(), new RegExp('\d+')];
```

此例中,Typescript推导的`arr` 的类型为 `(Date | RegExp)[]` 

### 上下文类型

TypeScript 使用变量的位置来推断其类型,这个机制称为上下文类型。例如:

```tsx
document.addEventListener('click', function (event) {
    console.log(event.button); // 
});
```

以上,Typescript知晓因为是`click`事件,`event`参数是`MouseEvent`的实例

当你改`click`事件为`scroll`事件时,typescript将会抛出一个错误:

```tsx
document.addEventListener('scroll', function (event) {
    console.log(event.button); // compiler error
});
```

报错:

```tsx
Property 'button' does not exist on type 'Event'.(2339)
```

Typescript知道这个`event`是一个`UIEvent`的实例,并不是一个`MouseEvent` 而`UIEvent`并没有`button`属性,因此会抛出一个错误.

‎在有些情况下，你会发现上下文类型，例如函数调用的参数、类型断言、对象和数组文本的成员、返回语句以及等式的右侧。‎

### 类型注释 vs. 类型推断

两者的不同之处

| 类型推断            | 类型注释                   |
| ------------------- | -------------------------- |
| Typescript 猜想类型 | 你准确的告诉Typescript类型 |

那应该什么时候使用类型推断或类型注释呢?

在实际中,你需要尽可能多的使用类型推断,在以下的情况使用类型注释:

- 当你声明一个变量,稍后才赋值
- 不能被推断的变量
- 返回`any`的函数,你需要明确返回值

### 总结

- ‎类型推断在初始化变量、设置参数默认值和确定函数返回类型时发生。‎
- ‎TypeScript 使用最佳通用类型算法来选择与所有变量兼容的最佳类型。‎
- ‎TypeScript 还使用上下文类型根据变量的位置推断变量的类型。‎





---



<p alt="center"><a alt="null" href="./index"><span alt="mt-icon">home</span></a> <p>



<div alt="fig">
<a href="https://github.com/Nico-M?tab=repositories" target="_blank" alt="null"><img src="https://img.shields.io/badge/-GitHub-181717?style=flat-square&logo=github"></a>
</div>











