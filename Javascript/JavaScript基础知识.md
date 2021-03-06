# JavaScript

#### 命名规范

* 严格区分大小写

* 使用数字、字母、下划线、$，数字不能作为开头

  ```javascript
  let $box; //=>一般用JQ获取的以$开头
  let _box; //=>一般公共变量都是_开头
  let 1box; //=>不可以，但是可以写box1
  ```

* 使用驼峰命名法：首字母小写，其余每一个有意义单词的首字母都要大写（命名尽可能语义化明显，使用英文单词）

  * 常用的缩写：add/insert/create/new（新增）、update（修改）、delete/del/remove/rm（删除）、sel/select/query/get（查询）、info（信息）...

* 不能使用关键字和保留字

#### 数据类型

- 基本数据类型
  - Number
  - String
  - Boolean
  - underfined
  - Null
- 引用数据类型
  - Object

#### Number

- 包含
  - 常规数字包括整数和浮点数(小数)
  - NaN
    - 不是一个数字，但是属于数字类型
    - NaN和任何数值(包括自己都不相等)
- 最大值最小值
  - 最大值   **Number.MAX_VALUE** 
  - 最小值   **Number.MIN_VALUE** 
  - 若number表示的数字超过了最大值则会返回一个Infinity(正无穷大)
- isNaN  可以检查一个值是否为有效数字，有效数字返回false，反之返回true。
  - 在使用isNaN 进行检测的时候，首先会验证检测的值是否是数字类型，如果不是，先基于Number()这个方法，把值转换为数字类型，然后再检测。
- 其他类型转换为Number
  - 字符串转换为数字类型
    - 只要字符串中包含有任意一个**非有效数字字符**(第一个点除外)，结果都是NaN。
    - 空字符串会变为数字零。
    - Number(纯数字的字符串)，进行转换。
  - 布尔转换为数字类型
    - true 转换为 1
    - false 转换为 0
  - Null转换为数字类型
    - null转换为 0
  - undefined 转换为数字类型
    - undefined 转换为 NaN
  - 引用数据类型转换为数字，是先把他基于toString方法转换为字符串，然后在转换为数字。
- parseInt/parseFloat([val],[进制])
  - 也是转换为数字的方法，对于字符串来说，他是从左到右一次查找有效数字字符，直到遇到非有效数字字符，停止查找(不管后面是否还有数字，不在查找)，把找到的当作数字返回。
  - parseInt（）把一个字符串中有效的整数内容转化为一个整数。
  - parseFloat（）把一个字符串转化为一个小数。作用：获得有效的小数。
- ==  在进行相等判断的时候也会转换为数字

#### String字符串数据类型

- 所有用单引号、双引号、反引号包起来的都是字符串

- 其他类型转换为字符串

  - [val].toString()
  - 字符串拼接
    - 四则运算法则中，除加法之外，其余都是数学计算，只有加法可能存在字符串拼接(一旦遇到字符串，不是数学运算，就是字符串拼接)。这是隐式的类型转换，由浏览器自动完成，实际上也是调用string()函数
  - null和undefined禁止直接转换为toString，调用会报错
  - 普通对象.toString()的结果是

  ```javascript
  "[object Object]"=>Objcet.prototype.toString方法不是转换为字符串的，而是用来检测数据类型的
  ```

  - String（）
    - 使用String（）函数做强制转换时对于number 和Boolean 实际上就是调用tostring（）方法。
    - 但是对于null和undefined就不会调用tostring（）方法，它会将null直接转换为"null",将undefined转换为"undefined"

#### Boolean 布尔数据类型

- 只有两个值   true/false

- 其他类型转换为布尔类型

  - 只有 0 、NaN、'' 、null 、undefined 五个之转换为false，其余转换为true(没有特殊情况)
  - Boolean([val])

  ```js
  console.log(Boolean(-1));  =>true
  ```

  - !/!!
    - ! ：取反(先转换为布尔，然后取反)
    - !!:   取反在取反，只相当于转换为布尔(先转换为布尔，然后取反，在取反)
  - 条件判断
    - 若条件只是一个值，不是==/===/！=/>=，是要转为布尔类型，然后验证真假

#### null和undefined的区别

- 都代表的是没有
  - null ：意料之中(一般都是开始不知道值，手动设置为null，后期在赋值)；
    - 一般用null作为初始空值，因为零不是空值，在栈内存中有一定的储存空间
  - undefined ：意料之外  (不是你所能决定的)
    - 创建一个变量没有赋值，默认值是undefined 

#### 运算符（操作符）

##### 算术运算符

* `+`   
  * 可以对两个值进行加法运算并将结果返回   
  * 对于非number值进行运算时，会将非number转换为number进行运算，注意：**任何值与NaN运算结果都为NaN**
  * 两个字符串相加 则会进行**拼串操作**
  * 任何与字符串进行加法操作 都会现将其余的数转换为字符串再与字符串进行拼串操作
  * 任何数据类型与空字符串进行加法运算，会把这个数据类型转换成字符串类型 
* `-`
  * 可以对两个值进行减法运算
* `*` 乘法    `/`除法
  * 任何值作`-/*`运算时都会自动转换为number
* %  取余

##### 一元运算符

* `+`正号
  * 不会对数字产生任何影响
* `-`负号
  * 可以对数字进行符号的取反
  * 对于非Number类型的值，它会将先转换为Number，然后在运算。可以对一个数据类型使用+使其转换为number类型。
* 自增("++")
  * 通过自增可以使变量在自身的基础上增加1。
  * 对于一个变量自增以后，原变量的值会改变
  * 分类
    * a++，将a的值先使用进行计算，计算后再加1。
    * ++a，将a的值先加1赋值给变量本身后再使用。
  * 无论是a++还是++a，每次调用一次都会使值增加1
* 自减("--")
  * 通过自减可以使变量在自身的基础上减1。
  * 分类
    * i--，将i的值先使用再减1赋值给变量i本身。
    * --i，将i的值先减1后赋值给变量i本身再使用。

##### 逻辑运算符

+ ！非(NOT)
  + 用来对一个值进行取反操作。
  + 如果对非布尔值进行操作，先转变成布尔值再取反。
  + 连续取反两次会，将其转换为布尔值
+ &&  与(AND)
  + 可以对符号两侧的值进行与运算并返回结果
  + 运算规则
    + 两个值中只要有一个值为false，值返回false；两个值都为true时，才会返回true。
      + 若第一个值为true，则必然返回第二个值
      + 若第一个值为false，则直接返回第一个值。
    + "&&"是短路的，如果第一个值为false就不会检查第二个值
+ || 或(OR)
  + 可以对符号两侧的值进行或运算，并返回结果
  + 运算规则
    + 两个值只要有一个true就返回true；两个值都为false才会返回false。
      + 若第一个值为true，则直接返回第一个值
      + 若第一个值为false，则返回第二个值。
    + "||"是短路的，若第一个值为true就不会返回第二个值

##### 赋值运算符

* = 可以将符号右侧的值赋值给符号左侧的变量

  ```javascript
  var a=10;
  +=  a + = 5 等价于 a = a + 5
  -=  a - = 5 等价于 a = a - 5
  *=  a * = 5 等价于 a = a * 5
  /=  a / = 5 等价于 a = a / 5
  %=  a % = 5 等价于 a = a % 5 //%取余数符号
  ```

##### 关系运算符

* 通过关系运算符可以比较两个运算符之间的关系，如果关系成立则返回true，反之返回false
* ` > >= < <=   `
  * 判断符号左侧的值是否大于(大于等于、小于、小于等于)右侧的，若关系成立返回true，反之返回false。
*   对于非数值进行比较时，先对字符串转换为数值，然后再进行比较，任何值与NaN比较都返回false。 
  *   注意：若符号两边的值都是字符串，则会比较两个字符的Unicode编码。比较字符编码时是一位一位的进行比较。 

##### 相等运算符

+ == 相等
  + 符号两侧进行比较，若相等就返回true，反之返回false。
  + 会对符号两侧的数据类型进行转换。
+ !=  不相等
  + 用来判断两个值是否不相等，若不相等返回true，否则返回false。
+ === 全等
  +  不会对两个值类型进行转换，直接判断，如果不同直接返回false，反之返回true。
+ !== 不全等
  +  用来判断两个值是否不全等，不会对类型自动转换 。

##### 条件(三元)操作符

* 简单的if/else的特殊处理方式

* 语法
  * 条件表达式？语句1(条件成立处理的事情)：语句2(不成立处理的事情)；
* 若处理的事情比较多，我们用括号包起来，每一件事情用逗号分隔
* 若不需要处理事情，可以使用null/undefined占位

##### 运算符优先级

* 一般来说，单目运算符优先级较高，赋值运算符优先级较低。算术运算符优先级较高，关系和逻辑运算符优先级较低。
* 多数运算符具有左结合性，单目运算符，三目运算符，赋值运算符具有右结合性。
* 若遇到优先级不清数可以使用（）来改变优先级。

#### 流程控制语句

##### 条件判断语句

* IF语句

  * 可以在执行某个语句之前进行判断，如果条件成立才会执行语句的条件不成立则语句不执行

  * 语法1：

    * if(条件表达式){语句........}
    * 条件表达式可任意多样性：等于、大于、小于的比较/一个值或者取反等 ，但最后结果都是要计算出是true还是false。

  * 语法2

    ```javascript
    if(条件表达式){
       语句.......
    }else{
        语句.......
    }
    ```

    * 会先对if后的条件表达式进行求值判断，若该值为true，则执行if后的语句，若该值为false，则执行else后的语句

  * 语法3：

    ```javascript
    if(条件表达式){
       语句.......
    }else if(条件表达式){
        语句.......
    }else{}
    ```

    * 会从上到下依次对条件表达式进行求值判断，若值为true，则执行当前语句。如果值为false，则继续向下判断；若所有的条件都不满足，则执行最后一个else中的语句。

##### 条件分支语句(switch)

* 语法

  ```javascript
  switch (条件表达式) {
  	case 表达式:
  		语句........
  		break;
  	case 表达式:
  		语句........
  		break;
  	default:
  		语句........
  }
  ```

* 执行流程

  * 在执行时会依次将case后的表达式和switch后的表达式的值进行**全等比较**。
  * 若比较结果为true，则从当前case处执行代码；反之接着向下比较。

* 每一种CASE情况结束后最好都加上BREAK。

  * 不加break，当前条件成立执行完成后，后面条件不论是否成立都要执行，直到遇到break为止。
  * 不加break可以实现变量在某些值的情况下做相同的事情。

* default等价于else，以上都不成立干的事情。

##### 循环语句

* FOR循环

  * 语法

    ```javascript
    for(1初始化表达式；2条件表达式；4更新表达式){
        3语句....
    }
    ```

  * 执行流程

    1. 创建循环初始值 
    2. 设置（验证）循环执行的条件
       * 若判断结果为true，则执行第三步；反之，种植循环。
    3. 条件成立执行循环体中的内容
    4. 当前循环结束后执行更新表达式，更新表达式执行完毕继续重复第二步。

* while循环

  * 语法

    ```javascript
    while（条件表达式）{
    语句…}
    ```

  * 执行流程

    * 先对条件表达式进行求值判断，如果值为true，则执行循环体，循环体执行完毕以后，继续对表达式进行判断如果为true，则继续执行循环体，以此类推，如果结果为false则终止执行。

* DO......while循环

  * 语法

    ```javascript
    do{  语句。。。
     }while（条件表达式）
    ```

  * 执行流程

    * do...while语句在执行时，会先执行循环体，循环体执行完毕以后，在对while后的条件表达式进行判断，如果结果为true，则继续执行循环体，执行完毕继续判断以此类推如果结果为false，则终止循环；

  * while是**先判断后执行**，而do...while会**先执行后判断**，do...while可以保证循环体至少执行一次，而while不能能。

* **break  continue**

  * continue

    *  默认对离他近的循环起作用 。
    * 结束当前这轮循环（continue后面的代码不再执行），继续执行下一轮循环。

  * break

    * 可以用来退出switch或循环语句,if语句中不能使用break。

    * 立即终止离他最近的那个循环语句。

    * 可以为循环语句创建一个labe1，来标识当前的循环

      labe1：循环语句

    *  强制结束整个循环（break后面代码也不再执行），而且整个循环直接结束。

#### Object

- {[key]:[value],.......}  任何一个对象都是由零到多组键值对（属性名：属性值）组成的，并且属性名不能重复 
- 分类
  - 内建对象
  - 宿主对象
  - 自定义对象
- 属性
  - 设置属性名属性值
    - 属性名不能重复，如果属性名已经存在，不属于新增属于修改属性值
  - 获取属性名对应的属性值
    - 对象 . 属性名
    - 对象[属性名]
    - 若属性名不存在，默认值的属性值是undefined  
    - 如果属性名是数字，则不能使用点的方式获取属性值
  - 添加属性
    - 对象 . 属性名=属性值
  - 删除属性
    - 真删除 ： 把属性彻底删掉 delete +属性名
    - 假删除 ： 属性还在值为空；值设置为null

#### Array

- 数组是特殊的对象数据类型
  - 中括号中设置的是属性值，属性名是默认生成的数字。
  - 默认属性length，存储数组的长度
  - 最后一项的索引是  数组长度-1
- 方法
  - push()
    - 该方法可以向数组的末尾添加一个或多个元素并返回新的数组长度
    - 将要添加的元素作为方法的参数传递，这样这些元素将会自动添加到数组的末尾
  - pop()
    - 该方法可以删除数组的最后一个元素，并将被删除的元素作为返回值返回
  - unshift()
    - 向数组开头添加一个或多个元素并返回新的数组长度
    - 插入元素后，其他元素会以此调整
  - shift()
    - 可以删除数组的第一个元素，并将被删除的元素作为返回值返回

#### 数据类型

*  基本数据类型直接在栈内存中存储，值与值之间独立存在，修改一个变量不会影响另一个变量 
*  引用数据类型，引用数据类型是直接保存在堆内存中，每创建一个新的对象，就会在堆内存中开辟一个新的空间，而变量保存的是对象的内存地址（对象的引用），如果两个变量保存的是同一个对象的引用，当通过一个变量修改属性时，另一个也会收到影响。 
*  当我们比较两个基本数据类型时，我们比较的是两个数值，当我们比较两个引用数据类型，比较的是两个内存地址 
*  JS中的变量都是保存在栈内存中的 

#### 数据类型的检测

- typeof[val] : 用来检车数据类型的运算符
  - 基于typeof检测出来的结果
    - 首先是一个字符串
    - 字符串中包含对应的类型 
  - 局限性
    - typeof null => "object"  但是null并不是对象
    - 基于type of无法细分出当前值是普通对象还是数组对象等，因为只要是对象数据类型，返回的结果都是"object"
- instanceof： 用来检测当前实例是否隶属于某个类
- constructor ： 基于构造函数检测数据类型
- Object.prototype.toString.call() :检测数据类型最适合的方法