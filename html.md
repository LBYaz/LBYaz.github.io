# Html学生用

## 简介

### 网页

#### 1.网页是什么

网页是网站中的一“页”，格式：HTML，它需要通过浏览器阅读

网页是构成网站的基本元素

尾缀 .htm或.html。所以俗称html文件

#### 2.html是什么

一种标记语言，不是编程语言

### 常用浏览器

火狐、谷歌、IE、Edge、Safari(苹果浏览器)...

## 开发工具Vscode

### vscode使用

- Ctrl+加号，Ctrl+减号，可以放大缩小视图
- 生成页面骨架结构：输入！按下Tab键
- 利用插件在浏览器预览：右键点击“Open In Default Browser”

## HTML标签

### 第一个HTML

- html页面中最大的标签，根标签

- head文档的头部，在head中必须设置的标签title

- title文档的标题，让网页有属于自己的网页标题

- body文档主体

  ![image-20260417170237425](imagehtml/image5.png)

- !DOCTYPE  文档类型声明，告诉浏览器使用哪种html版本显示网页（当前就是html5）

- lang语言种类：en为英语，zh-CN为中文

- 字符集（Character set）,通过meta标签的charset属性来规定HTML文档使用哪种字符编码，UTF-8

### HTML常用标签

#### 标题标签h1-h6

- 特点：1.加了标题的文字会变粗，字号也会依次变大

  ​            2.一个标题独占一行

![image-20260417170933270](imagehtml/image1)

#### 段落（p）

- p 标签用于定义段落

- 特点：1.文本在一个段落中可以根据浏览器窗口的大小进行自动换行

  ​            2.段落和段落之间保有空隙
  
  ![6](imagehtml/image6.png)![image-20260424155036834](imagehtml/image-7.png)

#### 换行标签(br)

- br,单词 break的缩写，意为打断、换行

- 特点：1.单标签

  ​            2.只是简单开始新的一行，段落之间会插入一些垂直的间距

  ![2](imagehtml/image-2.png)![3](imagehtml/image-3.png)

#### 水平线（hr）

- 可以设置属性：颜色color,宽度width（px是像素）,高度size,对齐方式（默认居中）align

![8](imagehtml/image-8.png)![9](imagehtml/image9.png)

![10](imagehtml/image-10.png)![image-20260424160003954](imagehtml/image-11.png)

![12](imagehtml/image-12.png)![13](imagehtml/image-13.png)

 提问

1.要实现一个文本换行，可以使用——标签

2.承载段落文本信息使用——标签

br

p

#### 文本格式化标签

- 加粗 strong或b

- 倾斜 em 或i

- 删除线 del 或s

- 下划线 ins 或u

![4](imagehtml/image4.png)

#### 标签之图片(img)

- src:路径
- alt:图片无法显示时候显示
- width:规定宽度
- height:高度
- title:鼠标悬停上面提示

![14](imagehtml/image-14.png)

 提问

1.img标签中alt属性的作用：       

2.以下哪个不是img标签的属性：src\alt\title\href

规定图像的代替文本

href

#### 图片的路径详解

- 绝对路径
- 相对路径
- 网络路径

![15](imagehtml/image-15.png)

#### 超文本链接(a)



