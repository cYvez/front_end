## 1.延迟加载js的方式有哪些以及区别
### 相同：script下载与HTML解析同时进行，相对于html解析来说都是异步的，区别在js的执行情况
  1. defer：等HTML全部解析完才会执行js代码，顺次执行js脚本
  ```
  <script defer type= "./script" src='script.js'></script>
  ```
  2. async：脚本的加载和执行是紧挨着的，不管声明顺序如何，只要加载完就会立即执行，且不顺次执行js脚本，谁先加载完先执行谁
    async 对于应用脚本的用处不大，因为它完全不考虑依赖（哪怕是最低级的顺序执行），不过它对于那些可以不依赖任何脚本或不被任何脚本依赖的脚本来说却是非常合适的，最典型的例子：Google Analytics

  ```
  <script async type= "./script" src='script.js'></script>
  ```
 [图文解析](https://blog.csdn.net/qq_41311259/article/details/120151261?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166908617916782414937502%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=166908617916782414937502&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-120151261-null-null.142^v66^control,201^v3^control_2,213^v2^t3_esquery_v1&utm_term=async%20defer&spm=1018.2226.3001.4187)
 
## 2. js数据类型有哪些：
  1. 基本类型：string，number，Boolean，undefined，null以及ES6新增的symbol，bignit
  2. 引用类型：object，date，array，RegExp
  3. 考题：
   
    alart(true+1);//=2
    alart('name'+true);//nametrue
    //字符串和其他类型相加变成字符串形式
    alart(undefined+1);//NaN,是一个数值类型，但不是具体的数
    alart(typeof null);//object
## 3. null和undefined区别
  + 这两个基本数据类型分别都只有⼀个值，就是 undefined 和 null。
  + undefined 代表的含义是未定义，null 代表的含义是空对象。⼀般变量声明了但还没有定
  义的时候会返回 undefined,null 主要⽤于赋值给⼀些可能会返回对象的变量，作为初始
  化。
  + undefined 在 js 中不是⼀个保留字，这意味着我们可以使⽤ undefined 来作为⼀个变量名，这样的做法是⾮常危险的，它会影响我们对 undefined 值的判断。但是我们可以
    **通过⼀些⽅法获得安全的 undefined 值，⽐如说 void 0**
  + null转化数值为0，undefined转化数值为NaN
  + 当我们对两种类型使⽤ typeof 进⾏判断的时候，Null 类型化会返回 “object”，这是⼀个历史遗留的问题。当我们使⽤双等号对两种类型的值进⾏⽐较时会返回 true，使⽤三个等
号时会返回 false。
## 4. 为啥typeof(null)是object？
  + 因为在JavaScript中，不同的对象都是使⽤⼆进制存储的，如果⼆进制前三位都是0的话，系统会判断为是Object类型，⽽null的⼆进制全是0，⾃然也就判断为
Object。
    + 000 对象
    + 1整型
    + 010 双精度类型
    + 100字符串
    + 110布尔类型
## 5. =和==和===区别
  + **它们最主要的区别在于 == 对⽐时，若类型不相等，会先转换为相同类型，然后再来⽐较值。⽽=== 则不会，只能在相同类型下⽐较值，不会做类型转换。还有⼀个是 =，这个是赋值，不是运算
符。**
  + ===这个⽐较简单。下⾯的规则⽤来判断两个值是否===相等：
    + 如果类型不同，就不相等
    + 如果两个都是数值，并且是同⼀个值，那么相等；(！例外)的是，如果其中⾄少⼀个是NaN，那么不相等。**（判断⼀个值是否是NaN，只能⽤ isNaN() 来判断）**
    + 如果两个都是字符串，每个位置的字符都⼀样，那么相等；否则不相等。
    + 如果两个值都是true，或者都是false，那么相等。
    + 如果两个值都引⽤同⼀个对象或函数，那么相等；否则不相等。
    + 如果两个值都是null，或者都是undefined，那么相等。
  + ==
    + 如果两个值类型相同，进⾏ === ⽐较。
    + 如果两个值类型不同，他们可能相等。根据下⾯规则进⾏类型转换再⽐较：（换成简单的；other to 数字；object to 基本）
      + 如果⼀个是null、⼀个是undefined，那么相等。
      + 如果⼀个是字符串，⼀个是数值，把字符串转换成数值再进⾏⽐较。
      + 如果任⼀值是 true ，把它转换成 1 再⽐较；如果任⼀值是 false，把它转换成 0 再⽐较。
      + 如果⼀个是对象，另⼀ 个是数值或字符串，把对象转换成基本类型的值再⽐较。对象转
      + 换成基本类型，利⽤它的 toString 或者 valueOf ⽅法。js 核⼼内置类，会尝试 valueOf
        先于 toString；例外的是 Date，Date利⽤的是toString转换。⾮ js 核⼼的对象，令说
        （⽐较麻烦，我也不⼤懂）
        任何其他组合，都不相等。
## 6. 微任务和宏任务
  + 

    
