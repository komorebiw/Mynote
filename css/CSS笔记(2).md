##### 文本标签

* `em`标签用于表示一段内容中的着重点
* `strong`标签用于表示一个内容的重要性
  * 这两个标签都表示一个强调的内容
  * em主要表示语气上的强调，em显示为斜体；strong表示强调的内容，比em更强烈，默认显示粗体。
  * 这两个标签可以单独使用也可以一起使用。
* `i` 标签中的内容会议斜体显示
* `b` 标签中的内容会以加粗显示
  - 没有具体的语义，h5规范中规定，对于不需要着重的内容单纯的加粗或者斜体用i和b
* `small` 标签中的内容会比它的父元素小一点。
  * 在h5使用small标签表示一些细则一类的内容，例如：合同中的小子，网站的版权声明等。
* `cite` 网页中所有加书名号的内容都可以使用cite标签，表示参考的内容。默认斜体。比如书名，歌名...
* `q` 标签 表示一个短的引用(行内引用)，浏览器会默认加上引号
* `blockquote` 标签表示一个长引用（块级引用）
  - 独占一行
* `sup` 使用sup设置上标 2<sup>2</sup>
* `sub` 下标2<sub>2</sub>
* `ins` 表示一个插入内容，`ins`里面的内容会自动添加下划线
* `del` 使用`del`标签表示一个删除的内容，`del`里的内容删除
* `pre` 是一个预格式标签，把代码放进`pre`，会保留代码的格式
* `code` 专门用来表示代码的，但是它不会保留格式

##### 有序列表和无序列表

* 无序列表
  * 使用`ul`标签来创建一个无序列表
  * 使用`li`在`ul`中创建一个一个的项
  * 通过type属性可以修改无序列表的项目符号
    * disc，默认值
    * square，实心的方块
    * circle，空心的圆圈
    * 默认的项目符号一般不使用，如需要设置项目符号，则可以采用为`li`设置背景图片的方式来设置。
  * `ul`和`li`都是块元素
* 有序列表
  * 使用`ol`来创建一个有序列表
  * 使用`li`在`ol`中创建一个一个的项
  * 通过type属性可以修改有序列表的项目符号
    * 1，默认值使用阿拉伯数字
    * a/A采用小写或大写字母作为序号
    * i/I采用小写或大写的罗马数字作为序号
  * 列表之间是可以互相嵌套的
* 定义列表
  * 用来对一些词汇或内容进行定义
  * 使用`dl`来创建一个定义列表
  * `dl`中有两个子标签
    * `dt`：被定义的内容
    * `dd`：对定义的内容的描述

##### 长度单位

* px像素
  * 像素是我们在网页中使用最多的一个单位
    * 一个像素就相当于我们在屏幕中的一个小点，我们的屏幕实际上就是由这些像素点构成的
  * 不同显示器一个像素大小也不相同，显示效果越好越清晰，像素就越小，反之像素越大。
* 百分比%
  * 可以将单位设置为一个百分比的形式，这样浏览器会根据**其父元素的样式来计算该值**
  * 当父元素的属性值发生变化时，子元素也会按照比例发生改变。创建一个自适应页面时，经常使用百分比做为单位。
* em
  * 和百分比类似，相对于**当前元素的字体大小**来计算
  * 1em=1font-size
  * 使用em时当字体大小发生改变时，em也会随之改变；设置字体相关的样式时，经常会使用em

##### 颜色单位

* 可以在css中直接使用颜色的单词来表示不同的颜色
* RGB值来表示不同的颜色
  * RGB值是通过red green blue三元色
    * 通过这三种颜色不同浓度来表示不同的颜色
  * 例rgb（红色的浓度，绿色的浓度，蓝色的浓度）
    * 颜色的浓度需要一个0~255之间的值。255表示最大，0表示没有
    * 浓度也可以采用百分数来设置，0%~100%之间的数字；
* RGBA ：
  * 就是在rgb的基础上增加一个a表示不透明度
  * 需要四个值，前三个值和rgb一样第四个表示透明度
    * 1 表示完全不透明  0 表示完全透明  .5半透明

* 十六进制的rgb值来表示颜色，原理和rgb原理一样，使用十六进制的数来代替，使用三组两位的十六进制数组来表示一个颜色，每组表示一个颜色
  * 语法：#红色绿色蓝色
  * 颜色浓度：00~ff，00表示没有相当于rgb中的0；ff表示最大相当于rgb中的255
    * 两两重复的颜色，可以简写。#0000ff可以简写为#00f
* HSL值 HSL值
  * H   色相 （0-360）
  * S  饱和度，颜色浓度（0%-100%）
  * L  亮度，颜色的亮度（0%-100%）

##### 字体样式

* 样式
  * 设置字体颜色，可以使用color来设置文字的颜色
  * 设置文字的大小，浏览器中一般默认文字大小都是16px
    * font-size设置并不是文字本身的大小，实际上是设置了格子的高度，因为在页面中每个文字都是处在一个看不见的框中的。
  * 通过font-family来设置文字的字体，该样式可以指定多个字体，当采用多个字体时浏览器会优先使用前边的字体，没有尝试下一个。
    * 当采用某种字体时如果浏览器支持则使用改字体，反之则使用默认字体
    * 浏览器使用的字体默认就是计算机中的字体
  * font-style可以设置文字的斜体
    * 可选值：normal  默认值  文字正常显示
    * italic  文字以斜体显示
    * oblique  文字会以倾斜的效果显示
    * 大部分浏览器不会倾斜和斜体做区分，所以italic和oblique效果是一样的
  * font-weight设置文本的粗细
    * normal  默认值文字正常显示
    * bold   文字加粗显示
    * 也可以指定100-900之间的9个值
  * font-variant设置小型大写字母（将所有的字母以大写形式显示，但是小写字母的大写，要比大写字母的大写小一些）
    * normal 默认值
    * small-caps文本以小型大写字母显示
  * font  可以同时设置字体相关的所有样式，可以将字体样式的值同时写在font样式中，不同值之间使用空格隔开
    * 设置样式时没有顺序要求甚至可以不写，不写则使用默认值。
    * 但是文字的大小和字体必须写，而且字体必须是最后一个样式，大小必须是倒数第二个样式
    * 使用简写会有一个比较好的性能
* 字体分类
  * serif(衬线字体)
  * sans-serif(非衬线字体)
  * monospace(等宽字体)
  * cursive(草书字体)
  * fantasy(虚幻字体)
  * 将字体设置为这些大的分类，浏览器会自动选择指定的字体并应用样式
  * 一般会将字体的分类指定为font-family中的最后一个字体

##### 行间距

* css中没有提供一个可以直接设置行间距的方式，只能通过设置行高来间接设置行间距，行高越大行间距越大
  * 行间距=行高-字体大小
* 使用line-height来间接设置行高
  * 可接收的值
    * 直接一个大小
    * 可以指定一个百分数，则会相对于字体去计算行高
    * 可以直接传入一个数值，则行高会设置字体大小的相应的倍数
  * 对于单行文本来说可以将行高设置为父元素的高度一致，这样可以使单行文本在父元素中垂直居中
* font也可以指定行高
  * 在字体大小后可以添加/行高，来指定行高，该值时可以选的如果不指定则会使用默认值
  * line-height样式不能设置在font前面否则样式会被覆盖掉

##### 文本样式

* text-transform可以设置文本的大小写
  * 可选值：
    * none 默认值，对文本不做任何处理
    * capitalize  单词的首字母大写。
    * uppercase 所有字母都大写
    * lowercase  所有字母都小写
* text-decoration可以设置文本的修饰
  * 可选值：
    * none 默认值，不做任何更改，正常显示
    * underline 为文本添加下划线
    * overline 为文本添加上划线
    * line-through 为文本添加删除线
  * 超链接的默认值是underline ，如需去除则设置为none
* letter-spacing可以指定字符间距
* word-spacing可以设置单词的间距；实际上就是设置词与词之间的空格大小
* text-align设置文本的对齐方式
  * 可选值：
    * left  默认值 文本靠左对齐
    * right  文本靠右对齐
    * center  文本居中对齐
    * justify  文本两端对齐，通过调整文本之间的空格大小来实现两端对齐目的
* text-indent设置文本的首行缩进
  * 指定一个正值，会向右缩进指定的像素
  * 指定一个负值，则会向左移动指定的像素
    * 通过这种方式可以将一些不想现实的文字隐藏起来