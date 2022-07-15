

# 2022/07/12 markdown语法学习

## 1.0 常规玩法

### 1.1 字体设置斜体、粗体、删除线

*这里是文字*
_这里是文字_
**这里是文字**
***这里是文字***
~~这里是文字~~

### 1.2 分级标题

\# 一级标题## 二级标题### 三级标题#### 四级标题##### 五级标题###### 六级标题  这个写法和 **文字**效果是一样的

### 1.3 链接

![测试一下图片](/Users/wjay/devTools/Git_Repository/Java-NoteBook-Tools/JavaSE/apic27858.jpeg)

### 1.4 分割线

 (任意三个减号、三个星号、等)

___

nihao 

***

niaho 

___

### 1.5 代码块

```java
import java.text.SimpleDateFormat;
import java.util.Date;

public class Main {
    public static void main(String[] args) {
        /*
        * 1.获取当前系统时间
        * 2.这里的Date类是java.util包下的
        * 3.默认输出的日期格式是国外的方式，因此通常需要对格式j进行转换
        * */
        Date date = new Date();
        System.out.println("当前系统日期="+date);
```

可以把文字放在这个符号里面，然后就会自动生成在代码块里面

`public class Main {
    public static void main(String[] args) {`

### 1.6 无序列表

（使用 *，+，- 表示无序列表）

* 你好
* 你好好
* 你好好好

### 1.7 有序列表

（使用数字和一个英文句点表示）

1. 你好
2.  你好
3.  你好
4.  你好
5.  你好
6. 你好

### 1.8 有序和无序一起用

### 1.9 表格

｜xxx｜xxx｜（用英文的竖线）

| 姓名 | 性别 |
| ---- | ---- |
|      |      |

| 姓名 | 性别 |
| ---- | ---- |
|      |      |

|姓名|性别|   --- 制作表格的语法

## 2.0 常用技巧{#index}

### 2.1 换行

方法1: 连续两个以上空格 + 回车

方法2: 使用html语言换行标签

### 2.2 缩进字符 

不断行的空白格 或 半角的空格 或 全角的空格 或

&nbsp;你好你好 （缩进1/4中文）

&ensp;你好你好 （缩进半个中文，1字符）

&emsp;你好你好（缩进1个中文，2字符）

你好你好 （未缩进）

### 2.3 特殊符号

（1）对于 Markdown 中的语法符号，前面加反斜线\即可显示符号本身。

&#10084;

\*

![fuhao](/Users/wjay/devTools/Git_Repository/Java-NoteBook-Tools/JavaSE/符号.png)

（2）其他特殊字符，示例如下：

![特殊符号](/Users/wjay/devTools/Git_Repository/Java-NoteBook-Tools/JavaSE/特殊符号.png)

想知道字符对应的Unicode码，可以看这个网站：https://unicode-table.com/cn/

### 2.4  字体、字号与颜色

![](/Users/wjay/devTools/Git_Repository/Java-NoteBook-Tools/JavaSE/字体、色号等.png)

<font color="DC143c">我是红色字体</font>

<img src="/Users/wjay/devTools/Git_Repository/Java-NoteBook-Tools/JavaSE/字体颜色二进制码.png" style="zoom:50%;" />

### 2.5链接的高级操作

<img src="/Users/wjay/devTools/Git_Repository/Java-NoteBook-Tools/JavaSE/apic27858.jpeg" style="zoom:25%;" />[test]



锚点

例子：跳转到[常用技巧](#index)

注脚

使用markdoen[^1]可以效率的书写文档，直接转换成HTML[^2]

[^1]:markdown是一种纯文本标记语言
[^2]:

1. 脚注自动被搬运到最后面，请到文章末尾查看，并且脚注后方的链接可以直接跳转回到加注的地方。
2. 由于简书不支持锚点，所以可以用注脚实现页面内部的跳转

### 2.6 背景色

Markdown本身不支持背景色设置，需要采用内置html的方式实现：借助 table, tr, td 等表格标签的 bgcolor 属性来实现背景色的功能。举例如下：

<table><tr><td bgcolor=orange>背景色是：orange</td></tr></table>

## 3.0 高端用法

### 3.1Late数学公式

**使用LaTex数学公式**

1.行内公式：使用两个”$”符号引用公式:

$公式$

2.行间公式：使用两对“$$”符号引用公式：



输入$\sqrt{x^{2}}$ 
显示结果是

具体可以参考 markdown编辑器使用LaTex数学公式（https://link.jianshu.com/?t=http%3A%2F%2Fblog.csdn.net%2Ftestcs_dn%2Farticle%2Fdetails%2F44229085）

latex数学符号详见：[常用数学符号的 LaTeX 表示方法](https://www.mohu.org/info/symbols/symbols.htm)

LaTex是什么？
LaTeX（LATEX，音译“拉泰赫”）是一种基于ΤΕΧ的排版系统，由美国计算机学家莱斯利·兰伯特（Leslie Lamport）在20世纪80年代初期开发，利用这种格式，即使使用者没有排版和程序设计的知识也可以充分发挥由TeX所提供的强大功能，能在几天，甚至几小时内生成很多具有书籍质量的印刷品。对于生成复杂表格和数学公式，这一点表现得尤为突出。因此它非常适用于生成高印刷质量的科技和数学类文档。这个系统同样适用于生成从简单的信件到完整书籍的所有其他种类的文档。

### 3.2 绘图





