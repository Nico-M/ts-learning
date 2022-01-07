## TS 集锦

1. 使用时遇到字面量

   ```typescript
   //Approch 1
   const req = {url:'/test',method:'GET' as 'GET'}
   //Approch 2
   const req = {url:'/test',method:'GET'} as const;
   
   handleRequest(req.url,req.method)
   //OR
   handleRequest(req.url,req.method as 'GET')
   ```

2. 动态的字面量

   ```typescript
   interface Alex {
   	name: string;
     age?: number;
     [key: string]: string
   }
   ```

3. 对于联合类型的narrow方式

   ```typescript
   //1. typeof
   if(typeof strs === 'object') {} // typeof null也是一个对象，要注意
   //2. 真性，通过if转译
   if(strs){} //对于有意义的0，‘’也会被过滤掉
   //3. 恒等于
   if(container.value != null) // 也可以过滤掉undefined
   //4. in运算
   if('swim' in animal){}
   //5. 实例 instanceof
   if(x instanceof Date){}
   //6. 类型预测
   function isFish(pet: Fish | Bird):pet is Fish{
     return (pet as Fish).swim !== undefined;
   }
   //7.discriminated union,通过共有属性判断
   interface Circle {
     kind:'circle';
     radius: number
   }
   interface Square {
     kind: 'square';
     sideLength: number
   }
   ```

4. 函数，具有属性的函数

   ```typescript
   type DescriptionFun = {
     description: string;
     (param: number):boolean  //可调用的
   }
   
   function doSth(fn: DescriptionFun){
     fn.description + ' returned' + fn(5)
   }
   ```

1. 一个类可以实现implements多个接口,implements只是对实现的接口类型进行check,并不会改变class的类型. 新类是同级的

2. extends, 拓展出一个子类,继承所有的属性和方法, 也可以用于拓展衍生类,==覆写其方法==(注意要包含原定义,>原来的定义,不是重写),衍生类永远也是基类的子类型.另外,初始化的顺序是 `基类field=>基类构造器=>衍生类field=>衍生类构造器` 

3. 可见性都是针对的==实例==,例如protected,只能在class内部和他的子类可见,但是在子类中是可以重新定义起可见性的, 而static成员则是针对==类==外部可访问的

4. 子类在constructor里面使用this时需要call `super()` 

5. 抽象类必须被继承实现才可以new,

6. 参数类型的判断:

   ```ts
   data instanceof window.Blob ||
   data instanceof window.FormData ||
   typeof data === 'string' || 
   data instanceof Array
   ```

   



---



<p alt="center"><a alt="null" href="./index"><span alt="mt-icon">home</span></a> <p>


<div alt="fig">
<a href="https://github.com/Nico-M?tab=repositories" target="_blank" alt="null"><img src="https://img.shields.io/badge/-GitHub-181717?style=flat-square&logo=github"></a>
</div>

