---
title: HTML的表格标签，列表标签，表单标签，HTML5有哪些新特性
author: Breezs
coverImg: /medias/banner/1.jpg
top: false
cover: false
toc: true
mathjax: false
tags:
    - 前端
    - HTML
categories:
    - 技能之树
reprintPolicy: cc_by
img: /medias/posts/17.jpg
date: 2022-03-11 16:13:10
summary:
abbrlink: 202203111613
password:
---

# HTML 的表格标签，列表标签，表单标签，HTML5 有哪些新特性

博客园主页：[博客园主页-冰山一树 Sankey](https://www.cnblogs.com/breezs)
CSDN 主页：[CSDN 主页-冰山一树 Sankey](https://blog.csdn.net/m0_59464010)

> 前端学习：学习地址：[黑马程序员 pink 老师前端入门教程，零基础必看的 h5(html5)+css3+移动](https://www.bilibili.com/video/BV14J4114768?from=search&seid=8917517766284511711)，下面这些都是一些学习笔记。临渊羡鱼，不如退而结网！！愿我自己学有所成，也愿每个前端爱好者学有所成

## 一. 表格标签

### 1.1 表格的主要作用

表格主要用于显示、展示数据，因为它可以让数据显示的非常的规整，可读性非常好。特别是后台展示数据的时候，能够熟练运用表格就显得很重要。一个清爽简约的表格能够把繁杂的数据表现得很有条理。

总结：表格不是用来布局页面的,而是用来展示数据的.

![image-20211030161905921](https://img-blog.csdnimg.cn/img_convert/db2e04b01f038165ce0b51a51175e0d8.png)

### 1.2 表格的基本语法

```html
<table>
    <tr>
        <td>单元格内的文字</td>
        ...
    </tr>
    ...
</table>
```

1. `<table> </table>` 是用于定义表格的标签。
2. `<tr> </tr>` 标签用于定义表格中的行，必须嵌套在 `<table> </table>`标签中。
3. `<td> </td>` 用于定义表格中的单元格，必须嵌套在`<tr></tr>`标签中。

```html
<table>
    <tr>
        <td>姓名</td>
        <td>性别</td>
        <td>年龄</td>
    </tr>
    <tr>
        <td>刘德华</td>
        <td>男</td>
        <td>30</td>
    </tr>
    <tr>
        <td>pink</td>
        <td>男</td>
        <td>21</td>
    </tr>
    <tr>
        <td>gff</td>
        <td>男</td>
        <td>21</td>
    </tr>
    <tr>
        <td>piwwecnk</td>
        <td>男</td>
        <td>21</td>
    </tr>
</table>
```

### 1.3 表头单元格标签

一般表头单元格位于表格的第一行或第一列，表头单元格里面的文本内容加粗居中显示, 突出重要性
`<th>` 标签表示 HTML 表格的表头部分(table head 的缩写)

![image-20220307231557954](https://img-blog.csdnimg.cn/img_convert/ea786150b30cca95313fc239443d6897.png)

语法：

```html
<table>
    <tr>
        <th>姓名</th>
        ...
    </tr>
    ...
</table>
```

### 1.4 表格属性

表格标签这部分属性实际开发不常用，后面通过 CSS 来设置.
**了解目的**:

1. 记住这些英语单词,后面 CSS 会使用.
2. 直观感受表格的外观形态

![image-20211030162742299](https://img-blog.csdnimg.cn/img_convert/11a38026072ca50abbddc38ce0714740.png)

### 1.5 案例分析

小说排行榜

![image-20211030162815069](https://img-blog.csdnimg.cn/img_convert/f641d3fd1eade1d4a5f77db7ebe6336d.png)

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <meta http-equiv="X-UA-Compatible" content="ie=edge" />
        <title>今日小说排行榜</title>
    </head>
    <body>
        <table
            align="center"
            width="500"
            height="249"
            border="1"
            cellspacing="0"
        >
            <thead>
                <tr>
                    <th>排名</th>
                    <th>关键词</th>
                    <th>趋势</th>
                    <th>进入搜索</th>
                    <th>最近七日</th>
                    <th>相关链接</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>1</td>
                    <td>鬼吹灯</td>
                    <td><img src="down.jpg" /></td>
                    <td>456</td>
                    <td>123</td>
                    <td>
                        <a href="#">贴吧</a> <a href="#">图片</a>
                        <a href="#">百科</a>
                    </td>
                </tr>

                <tr>
                    <td>1</td>
                    <td>鬼吹灯</td>
                    <td><img src="down.jpg" /></td>
                    <td>456</td>
                    <td>123</td>
                    <td>
                        <a href="#">贴吧</a> <a href="#">图片</a>
                        <a href="#">百科</a>
                    </td>
                </tr>
                <tr>
                    <td>3</td>
                    <td>西游记</td>
                    <td><img src="up.jpg" /></td>
                    <td>456</td>
                    <td>123</td>
                    <td>
                        <a href="#">贴吧</a> <a href="#">图片</a>
                        <a href="#">百科</a>
                    </td>
                </tr>
                <tr>
                    <td>1</td>
                    <td>鬼吹灯</td>
                    <td><img src="down.jpg" /></td>
                    <td>456</td>
                    <td>123</td>
                    <td>
                        <a href="#">贴吧</a> <a href="#">图片</a>
                        <a href="#">百科</a>
                    </td>
                </tr>
                <tr>
                    <td>1</td>
                    <td>鬼吹灯</td>
                    <td><img src="down.jpg" /></td>
                    <td>456</td>
                    <td>123</td>
                    <td>
                        <a href="#">贴吧</a> <a href="#">图片</a>
                        <a href="#">百科</a>
                    </td>
                </tr>
                <tr>
                    <td>1</td>
                    <td>鬼吹灯</td>
                    <td><img src="down.jpg" /></td>
                    <td>456</td>
                    <td>123</td>
                    <td>
                        <a href="#">贴吧</a> <a href="#">图片</a>
                        <a href="#">百科</a>
                    </td>
                </tr>
            </tbody>
        </table>
    </body>
</html>
```

### 1.6 表格结构标签

使用场景:因为表格可能很长,为了更好的表示表格的语义，可以将表格分割成 表格头部和表格主体两大部分.
在表格标签中，分别用：`<thead>`标签 表格的头部区域、`<tbody>`标签 表格的主体区域. 这样可以更好的分清表格结构。

![image-20211030165324934](https://img-blog.csdnimg.cn/img_convert/f040926e2efb13c78583936c2a6d014f.png)

1. `<thead></thead>`：用于定义表格的头部。<thead> 内部必须拥有 <tr> 标签。 一般是位于第一行。
2. `<tbody></tbody>`：用于定义表格的主体，主要用于放数据本体 。
3. 以上标签都是放在 `<table></table>` 标签中。

### 1.7 合并单元格

特殊情况下,可以把多个单元格合并为一个单元格。

![image-20211030165422674](https://img-blog.csdnimg.cn/img_convert/101f40e6cdeb96840eb95776897f832c.png)

**跨行合并：rowspan ＝"合并单元格的个数"**

**跨列合并：colspan ＝"合并单元格的个数"**

![image-20220308105829927](https://img-blog.csdnimg.cn/img_convert/b120fdfbce120ee19c214c6472de66e6.png)

目标单元格：（写合并代码）

-   跨行：最上侧单元格为目标单元格，写合并代码
-   跨列：最左侧单元格为目标单元格，写合并代码

![image-20220308110010946](https://img-blog.csdnimg.cn/img_convert/63a9053e6c6b56417fc151778e41b407.png)

**合并单元格三步曲**：

1. 先确定是跨行还是跨列合并。
2. 找到目标单元格. 写上合并方式 = 合并的单元格数量。比如：`<td colspan="2"></td>`。
3. 删除多余的单元格。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>合并单元格</title>
</head>
<body>
    <table width="500" height="249" border="1" cellspacing="0">
        <tr>
            <td></td>
            <td colspan="2"></td>
            <-->原来单元格</-->
        </tr>
        <tr>
            <td rowspan="2"></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
           	<-->原来单元格</-->
            <td></td>
            <td></td>
        </tr>

    </table>
</body>
</html>
```

![image-20211030170600292](https://img-blog.csdnimg.cn/img_convert/2a21df5d729f1c5adf7c2b45e9c02a15.png)

## 二. 列表标签

**表格**是用来显示数据的，那么**列表**就是用来布局的。
列表最大的特点就是**整齐、整洁、有序**，它作为布局会更加自由和方便。
根据使用情景不同，列表可以分为三大类：**无序列表、有序列表和自定义列表。**

|   标签名    |    定义    |                              说明                              |
| :---------: | :--------: | :------------------------------------------------------------: |
| `<ul></ul>` |  无序标签  |  里面只能包含 li，设有顺序，使用较多。li 里面可以包含任何标签  |
| `<li></li>` |  有序标签  | 里面只能包含 li，有顺序，使用相对较少。li 里面可以包含任何标签 |
| `<dl><dl>`  | 自定义列表 |       里面只能包含 dt 和 dd。dt 和 dd 里面可以放任何标签       |

![image-20211030200121048](https://img-blog.csdnimg.cn/img_convert/cb1728a7f0216abca5f23f846c0235f9.png)

### 2.1 无序列表

`<ul>` 标签表示 HTML 页面中项目的无序列表，一般会以项目符号呈现列表项，而列表项使用 `<li>` 标签定义。
无序列表的基本语法格式如下：

```html
<ul>
    <li>列表项1</li>
    <li>列表项2</li>
    <li>列表项3</li>
    ...
</ul>

<ul>
    <li>榴莲</li>
    <li>臭豆腐</li>
    <li>鲱鱼罐头</li>
</ul>
```

**注意**：

1. 无序列表的各个列表项之间没有顺序级别之分，是并列的。
2. `<ul>\</ul>` 中只能嵌套 `<li>\</li>`，直接在 `<ul>\</ul>` 标签中输入其他标签或者文字的做法是不被允许的
3. `<li>` 与 `</li>` 之间相当于一个容器，可以容纳所有元素。
4. 无序列表会带有自己的样式属性，但在实际使用时，我们会使用 CSS 来设置。

### 2.2 有序列表

有序列表即为有排列顺序的列表，其各个列表项会按照一定的顺序排列定义。
在 HTML 标签中，`<ol>` 标签用于定义有序列表，列表排序以数字来显示，并且使用 `<li>` 标签来定义列表项。
有序列表的基本语法格式如下：

```html
<ol>
    <li>列表项1</li>
    <li>列表项2</li>
    <li>列表项3</li>
    ...
</ol>
```

1. `<ol>\</ol>`中只能嵌套`<li>\</li>`，直接在`<ol>\</ol>`标签中输入其他标签或者文字的做法是不被允许的。

2. `<li>` 与 `</li>`之间相当于一个容器，可以容纳所有元素。
3. 有序列表会带有自己样式属性，但在实际使用时，我们会使用 CSS 来设置。

### 2.3 自定义列表

自定义列表的使用场景:
自定义列表常用于对术语或名词进行解释和描述，定义列表的列表项前没有任何项目符号。

![image-20220308110610436](https://img-blog.csdnimg.cn/img_convert/877636a091651aec5a0d9202a8956f87.png)

在 HTML 标签中，`<dl>` 标签用于定义描述列表（或定义列表），该标签会与 `<dt>`（定义项目/名字）和`<dd>`（描述每一个项目/名字）一起使用。
其基本语法如下：

```html
<dl>
    <dt>名词1</dt>
    <dd>名词1解释1</dd>
    <dd>名词1解释2</dd>
</dl>
```

1. `<dl></dl>` 里面只能包含 `<dt>` 和 `<dd>。`
2. `<dt>` 和 `<dd>`个数没有限制，经常是一个`<dt>` 对应多个`<dd>`。

![image-20211030201423280](https://img-blog.csdnimg.cn/img_convert/466ac1b8a6d6724a0882f04f987d6d60.png)

## 三. 表单标签

使用表单目的是为了收集用户信息。

在我们网页中， 我们也需要跟用户进行交互，收集用户资料，此时就需要表单。

网页中的表单展示

![image-20220308110715652](https://img-blog.csdnimg.cn/img_convert/781d3f77a37f8f245e544e6d27b0a4ec.png)

### 3.1 表单的组成

在 HTML 中，一个完整的表单通常由表单域、表单控件（也称为表单元素）和 提示信息 3 个部分构成。

![image-20220308110827095](https://img-blog.csdnimg.cn/img_convert/223c44c4eb6ca09324983b3c1e76f1d5.png)

### 3.2 表单域

表单域是一个包含表单元素的区域。
在 HTML 标签中， `<form></form>` 标签用于定义表单域，以实现用户信息的收集和传递。

`<form>` 会把它范围内的表单元素信息提交给服务器

```html
<form action=“url地址” method=“提交方式” name=“表单域名称">
各种表单元素控件
</form>
```

**常用属性**:

|  属性  |  属性值   |                         作用                         |
| :----: | :-------: | :--------------------------------------------------: |
| action | url 地址  | 用于指定接收并处理表单数据的服务器程序的 url 地址。  |
| method | get／post |  用于设置表单数据的提交方式，其取值为 get 或 post。  |
|  name  |   名称    | 用于指定表单的名称，以区分同一个页面中的多个表单域。 |

### 3.3 表单控件

#### 3.3.1 \<input>标签

在英文单词中，input 是输入的意思，而在表单元素中 `<input/>` 标签用于收集用户信息。
在 `<input/>` 标签中，包含一个 type 属性，根据不同的 type 属性值，输入字段拥有很多种形式（可以是文本、字段、复选框、掩码后的文本控件、单选按钮、按钮等）。

```html
input type="属性值" />
```

-   `<input/>` 标签为单标签
-   type 属性设置不同的属性值用来指定不同的控件类型

type 属性的属性值及其描述如下：

|  属性值  |                               描述                               |
| :------: | :--------------------------------------------------------------: |
|  button  |    定义可点击按钮（多数情况下，用于通过 JavaScript 启动脚本）    |
| checkbox |                           定义复选框。                           |
|   file   |             定义输入字段和＂浏览＂按钮，供文件上传。             |
|  hidden  |                       定义隐藏的输入字段。                       |
|  image   |                     定义图像形式的提交按钮。                     |
| password |               定义密码字段。该字段中的字符被掩码。               |
|  radio   |                          定义单选按钮。                          |
|  reset   |          定义重置按钮。重置按钮会清除表单中的所有数据。          |
|  submit  |         定义提交按钮。提交按钮会把表单数据发送到服务器。         |
|   text   | 定义单行的输入字段，用户可在其中输入文本。默认宽度为 20 个字符。 |

除 type 属性外，`<input>`标签还有其他很多属性，其常用属性如下：

|   属性    | 属性值       | 描述                                    |
| :-------: | ------------ | --------------------------------------- |
|   name    | 由用户自定义 | 定义 input 元素的名称。                 |
|   value   | 由用户自定义 | 规定 input 元素的值。                   |
|  checked  | checked      | 规定此 input 元素首次加载时应当被选中。 |
| maxlength | 正整数       | 规定输入字段中的字符的最大长度。        |

1. name 和 value 是每个表单元素都有的属性值,主要给后台人员使用.
2. name 表单元素的名字, 要求 单选按钮和复选框要有相同的 name 值.
3. checked 属性主要针对于单选按钮和复选框, 主要作用一打开页面,就要可以默认选中某个表单元素.
4. maxlength 是用户可以在表单元素输入的最大字符数, 一般较少使用.

**小问答：**

1. **有些表单元素想刚打开页面就默认显示几个文字怎么做?**

    ```html
    用户名: <input type="text" value="请输入用户名" />
    ```

    答: 可以给这些表单元素设置 value 属性=“值”

2. **页面中的表单元素很多，如何区别不同的表单元素?**

```html
用户名: <input type="text" value="请输入用户名" name="username" />
```

答: name 属性：当前 input 表单的名字，后台可以通过这个 name 属性找到这个表单。页面中的表单很多，name 的主要作用就是用于区别不同的表单。

-   name 属性后面的值，是自定义的
-   radio (或者 checkbox）如果是一组，必须给他们命名相同的名字

```html
<input type="radio" name="sex" />男 <input type="radio" name="sex" />女
```

3. **. 如果页面一打开就让某个单选按钮或者复选框是选中状态?**

答: checked 属性：表示默认选中状态。用于单选按钮和复选按钮

```html
性 别: <input type="radio" name="sex" value="男" checked="checked" />男
<input type="radio" name="sex" value="女" />女
```

4. **如何让 input 表单元素展示不同的形态? 比如单选按钮或者文本框**

答: type 属性：type 属性可以让 input 表单元素设置不同的形态

```html
<input type="radio" name="sex" value="男" checked="checked" />男
<input type="text" value="“请输入用户名”" />
```

总结：

```html
<form action="xxx.php" method="get">
    <!-- text 文本框 用户可以里面输入任何文字 -->
    用户名:
    <input type="text" name="username" value="请输入用户名" maxlength="6" />
    <br />
    <!-- password 密码框 用户看不见输入的密码 -->
    密码: <input type="password" name="pwd" /> <br />
    <!-- radio 单选按钮  可以实现多选一 -->
    <!-- name 是表单元素名字 这里性别单选按钮必须有相同的名字name 才可以实现多选1 -->
    <!-- 单选按钮和复选框可以设置checked 属性, 当页面打开的时候就可以默认选中这个按钮 -->
    性别: 男 <input type="radio" name="sex" value="男" /> 女
    <input type="radio" name="sex" value="女" checked="checked" /> 人妖
    <input type="radio" name="sex" value="人妖" /> <br />
    <!-- checkbox 复选框  可以实现多选 -->
    爱好: 吃饭 <input type="checkbox" name="hobby" value="吃饭" /> 睡觉
    <input type="checkbox" name="hobby" /> 打豆豆
    <input type="checkbox" name="hobby" checked="checked" />
    <br />
    <!-- 点击了提交按钮,可以把 表单域 form 里面的表单元素 里面的值 提交给后台服务器 -->
    <input type="submit" value="免费注册" />
    <!-- 重置按钮可以还原表单元素初始的默认状态 -->
    <input type="reset" value="重新填写" />
    <!-- 普通按钮 button  后期结合js 搭配使用-->
    <input type="button" value="获取短信验证码" /> <br />
    <!-- 文件域 使用场景 上传文件使用的 -->
    上传头像: <input type="file" />
</form>
```

#### 3.3.2 \<label>标签

`<label>` 标签为 input 元素定义标注（标签）。
`<label>` 标签用于绑定一个表单元素, 当点击`<label>` 标签内的文本时，浏览器就**会自动将焦点(光标)转到或者选择对应的表单元素**上,增加选取范围，用来增加用户体验.
**语法**：

```html
<label for="sex">男</label> <input type="radio" name="sex" id="sex" />
```

**核心**： 标签的 for 属性应当与相关元素的 id 属性相同。

#### 3.3.3 \<select>标签

使用场景: 在页面中，如果有多个选项让用户选择，并且想要节约页面空间时，我们可以使用\<select>标签控件定义下拉列表。

![image-20211030210332863](https://img-blog.csdnimg.cn/img_convert/3b63d689b5e0e367f1bbbb8dace2ff23.png)

在页面中，如果有多个选项让用户选择，并且想要节约页面空间时，我们可以使用`<select>`标签控件定义下拉列表

**语法**：

```html
<select>
    <option>选项1</option>
    <option>选项2</option>
    <option>选项3</option>
    ...
</select>
```

1. `<select>` 中至少包含一对`<option>` 。
2. 在`<option>` 中定义 `selected =“ selected "` 时，当前项即为默认选中项。

#### 3.3.4 \<textarea>标签

当用户输入内容较多的情况下，我们就不能使用文本框表单了，此时我们可以使用 `<textarea>` 标签。
在表单元素中，`<textarea>` 标签是用于定义多行文本输入的控件。

使用多行文本输入控件，可以输入更多的文字，该控件常见于留言板，评论。

**语法**：

```html
<textarea rows="3" cols="20">
 文本内容
</textarea>
```

1. 通过 `<textarea>` 标签可以轻松地创建多行文本输入框。
2. **cols=“每行中的字符数”** ，**rows=“显示的行数”**，我们在实际开发中不会使用，都是用 CSS 来改变大小。

### **表格，列表，表单综合案例**

![image-20211030215235761](https://img-blog.csdnimg.cn/img_convert/01dcf073939c46b8ae8aaa7f0d9704f0.png)

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <meta http-equiv="X-UA-Compatible" content="ie=edge" />
        <title>综合案例-注册页面</title>
    </head>
    <body>
        <h4>青春不常在，抓紧谈恋爱</h4>
        <table width="600">
            <!-- 第一行 -->
            <tr>
                <td>性别:</td>
                <td>
                    <input type="radio" name="sex" id="nan" />
                    <label for="nan"> <img src="images/man.jpg" /> 男 </label>
                    <input type="radio" name="sex" id="nv" />
                    <label for="nv"><img src="images/women.jpg" /> 女</label>
                </td>
            </tr>
            <!-- 第二行 -->
            <tr>
                <td>生日:</td>
                <td>
                    <select>
                        <option>--请选择年份--</option>
                        <option>2001</option>
                        <option>2002</option>
                        <option>2003</option>
                    </select>
                    <select>
                        <option>--请选择月份--</option>
                        <option>1</option>
                        <option>2</option>
                        <option>3</option>
                    </select>
                    <select>
                        <option>--请选择日--</option>
                        <option>1</option>
                        <option>2</option>
                        <option>3</option>
                    </select>
                </td>
            </tr>
            <!-- 第三行 -->
            <tr>
                <td>所在地区</td>
                <td><input type="text" value="北京思密达" /></td>
            </tr>
            <!-- 第四行 -->
            <tr>
                <td>婚姻状况:</td>
                <td>
                    <input type="radio" name="marry" checked="checked" />未婚
                    <input type="radio" name="marry" /> 已婚
                    <input type="radio" name="marry" /> 离婚
                </td>
            </tr>
            <!-- 第五行 -->
            <tr>
                <td>学历:</td>
                <td><input type="text" value="博士后" /></td>
            </tr>
            <!-- 第六行 -->
            <tr>
                <td>喜欢的类型:</td>
                <td>
                    <input type="checkbox" name="love" /> 妩媚的
                    <input type="checkbox" name="love" /> 可爱的
                    <input type="checkbox" name="love" /> 小鲜肉
                    <input type="checkbox" name="love" /> 老腊肉
                    <input type="checkbox" name="love" checked="checked" />
                    都喜欢
                </td>
            </tr>
            <!-- 第七行 -->
            <tr>
                <td>个人介绍</td>
                <td>
                    <textarea>个人简介</textarea>
                </td>
            </tr>
            <!-- 第八行 -->
            <tr>
                <td></td>
                <td>
                    <input type="submit" value="免费注册" />
                </td>
            </tr>
            <tr>
                <td></td>
                <td>
                    <input type="checkbox" checked="checked" />
                    我同意注册条款和会员加入标准
                </td>
            </tr>
            <tr>
                <td></td>
                <td>
                    <a href="#"> 我是会员，立即登录</a>
                </td>
            </tr>
            <tr>
                <td></td>
                <td>
                    <h5>我承诺</h5>
                    <ul>
                        <li>年满18岁、单身</li>
                        <li>抱着严肃的态度</li>
                        <li>真诚寻找另一半</li>
                    </ul>
                </td>
            </tr>
        </table>
    </body>
</html>
```

## 四. HTML5 新特性

HTML5 的新增特性主要是针对于以前的不足，增加了一些新的标签、新的表单和新的表单属性等。
这些新特性都有兼容性问题，基本是 IE9+ 以上版本的浏览器才支持，如果不考虑兼容性问题，可以大量使用这些新特性。
声明：

1. 新特性增加了很多，但是我们专注于开发常用的新特性。
2. 基础班我们讲解部分新特性，到了就业班还会继续讲解其他新特性。

### 1.1 新增的语义化标签

以前布局，基本用 div 来做。div 对于搜索引擎来说，是没有语义的。

```css
<div class=“header”> </div>
<div class=“nav”> </div>
<div class=“content”> </div>
<div class=“footer”> </div>
```

![image-20211120103632203](https://img-blog.csdnimg.cn/img_convert/7e58b6b537782c50f9961978f96fd687.png)

### 1.2 新增 video 标签

HTML5 在不使用插件的情况下，也可以原生的支持视频格式文件的播放，当然，支持的格式是有限的。

![image-20211120155411703](https://img-blog.csdnimg.cn/img_convert/8ae5f99a6e725a3dfa3a40a7e6d3d37e.png)

语法：

```
<video src="文件地址" controls="controls"></video>
```

```
 <video controls="controls" width="300">
 <source src="move.ogg" type="video/ogg" >
 <source src="move.mp4" type="video/mp4" >
 您的浏览器暂不支持 <video> 标签播放视频
 </ video >
```

**常见属性**：

| 属性     | 值                                        | 描述                                                          |
| -------- | ----------------------------------------- | ------------------------------------------------------------- |
| autoplay | autoplay                                  | 视频就堵自动幅放(谷欧刘览器需要添加 muted 来解决自动插放问题) |
| controls | controls                                  | 向用户显示播放控件                                            |
| width    | pixels(像素)                              | 设置播放器宽度                                                |
| height   | pixels(像素)                              | 设置播放器高度                                                |
| loop     | loop                                      | 插放完是香继续插放该视频,循环插放                             |
| preload  | aut0(预先加载视频)<br/>none(不应加载视频) | 规定是否预加载视须如果有了 autoplay 就忽略该属性)             |
| src      | url                                       | 视频 ur 地址                                                  |
| poster   | Imgurl                                    | 加载等待的画面图片                                            |
| muted    | muted                                     | 静音播放                                                      |

### 1.3 新增 audio 标签

| 浏贷器           | MP3 | Wav | Ogg |
| ---------------- | --- | --- | --- |
| Intemet Explorer | YES | NO  | NO  |
| Chrome           | YES | YES | YES |
| Firefox          | YES | YES | YES |
| Safari           | YES | YES | NO  |
| Opera            | YES | YES | YES |

语法：

<audio src="文件地址" controls="controls"></audio>

```
<audio src="文件地址" controls="controls"></audio>
```

```
 <source src="happy.mp3" type="audio/mpeg" >
 <source src="happy.ogg" type="audio/ogg" >
 您的浏览器暂不支持 <audio> 标签。
 </ audio>
```

**常见属性**

| 属性     | 值       | 描述                                           |
| -------- | -------- | ---------------------------------------------- |
| autoplay | autoplay | 如果出现该属性,则音频在就绪后马上播放。        |
| controls | controls | 如果出现该属性,则向用户显示控件,比如播放按钮。 |
| loop     | loop     | 如果出现该属性,则每当音频结束时重新开始插放。  |
| src      | url      | 要播放的音频的 URL,                            |

谷歌浏览器把音频和视频自动播放都禁止了。

**总结**：

-   音频标签和视频标签使用方式基本一致
-   浏览器支持情况不同
-   谷歌浏览器把音频和视频自动播放禁止了
-   我们可以给视频标签添加 muted 属性来静音播放视频，音频不可以（可以通过 JavaScript 解决）
-   视频标签是重点，我们经常设置自动播放，不使用 controls 控件，循环和设置大小属性

### 1.4 新增的 input 类型

| 属性值        | 说明                          |
| ------------- | ----------------------------- |
| type="email"  | 限制用户输入必须为 Email 类型 |
| type="url"    | 限制用户输入必须为 URL 类型   |
| type="date"   | 限制用户输入必须为日期类型    |
| type="time"   | 限制用户输入必须为时间类型    |
| type="month"  | 限制用户输入必须为月类型      |
| type="week"   | 限制用户输入必须为周类型      |
| type="number" | 限制用户输入必须为数字类型    |
| type="tel"    | 手机号码                      |
| type="search" | 搜索框                        |
| type="color"  | 生成一个颜色选择表单          |

### 1.5 新增表单属性

| 属性         | 值        | 说明                                                                                                                                                                                        |
| ------------ | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| required     | required  | 表单拥有该属性表示其内容不能为空,必填                                                                                                                                                       |
| placeholder  | 提示文本  | 表单的提示信息,存在默认值将不显示                                                                                                                                                           |
| autofocus    | autofocus | 自动聚焦属性,页面加载完成自动聚焦到指定表单                                                                                                                                                 |
| autocomplete | off /on   | 当用户在字段开始键入时,浏览器基于之前键入过的值,应该显示出在字段中填写的选项。默认已经打开,如 autocomplete="on",关闭 autocomplete="off <br />需要放在表单内,同时加上 name 属性,同时成功提交 |
| multiple     | multiple  | 可以多选文件提交                                                                                                                                                                            |

```
可以通过以下设置方式修改placeholder里面的字体颜色:
input:placeholder{
	color:pink;
}

```
