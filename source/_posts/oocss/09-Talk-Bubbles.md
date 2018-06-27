title: 09、对话框（Talk Bubbles）
categories: [理论, css, oocss]
tags: [理论, css, oocss]
date: 2018/06/27 21:30:00
---

[原文](https://github.com/stubbornella/oocss/wiki/Talk-Bubbles)

Talk bubbles were created to give context specific help, however they may be used for other purposes like blog comments, cartoon-style talk bubbles, etc. 

对话框是为了给文章的特定内容添加帮助信息而创建的，也可以用于其他目的，如博客评论，卡通式对话框等。

<a href="http://www.flickr.com/photos/nicole_hugo/3897449437/" title="Talk Bubbles by Stubbornella (aka Nicole), on Flickr"><img src="http://farm4.static.flickr.com/3506/3897449437_6b0fe48b29_o.png" width="322" height="196" alt="Talk Bubbles" /></a>

- No images required
- Secondary elements in place to allow for borders (just make the lower b a bit larger and set the border color)
- Easy to adapt the size of the arrow
- Compatible with border-radius generated rounded corners
- Base CSS objects are 1K
- IE6 uses page background color for the transparent bits because it doesn't support the color keyword "transparent"
- Allows eight different arrow positions





- 不依赖图片
- 箭头接触的位置可以设置边框（将箭头调大一些并设置颜色即可）
- 易于调整光标箭头的大小
- 兼容边框圆角
- 基本的CSS对象只有1K
- IE6使用页面背景颜色实现透明效果，因为它不支持color关键字“transparent”
- 支持8种不同的箭头位置

<a href="http://www.flickr.com/photos/nicole_hugo/3898006763/" title="Speech Bubble Pointer positions by Stubbornella (aka Nicole), on Flickr"><img src="http://farm3.static.flickr.com/2452/3898006763_07e964665b_o.png" width="472" height="187" alt="Speech Bubble Pointer positions" /></a>

## 基础类（Base Classes）
| Property      | Description                            |
| ------------- | ------------------------------------   |
| `bubble` | Applied to the mod wrapper, this is the base class for all talk bubbles. To change the size of the pointer edit this class (margin and border width should always be equal). |
| `bubbleTop` | Structural class that extends `.bubble`, positions the pointer at the top of the module. |
| `bubbleRight` | Structural class that extends `.bubble`, positions the pointer at the right of the module. |
| `bubbleBottom` | Structural class that extends `.bubble`, positions the pointer at the bottom of the module. |
| `bubbleLeft` | Structural class that extends `.bubble`, positions the pointer at the left of the module. |
| `bubbleHorizontalExt` | A class which can be used in conjunction with `.bubbleLeft` or `.bubbleRight` to move the talk pointer to the bottom portion of the left or right sides  |
| `bubbleVerticalExt` | A class which can be used in conjunction with `.bubbleTop` or `.bubbleBottom` to move the talk pointer to the right edge of the top or bottom sides   |



| 属性      | 描述                            |
| ------------- | ------------------------------------   |
| `bubble` | 应用于mod容器，这是所有对话框的基类。 如果您要改变箭头的大小，请您编辑这个类（外边距和边框宽度应该是相等的）。 |
| `bubbleTop` | 扩展`.bubble`的结构类，会将箭头置于模块的顶部。|
| `bubbleRight` | 扩展`.bubble`的结构类，会将箭头置于模块的右部。 |
| `bubbleBottom` | 扩展`.bubble`的结构类，会将箭头置于模块的下部。 |
| `bubbleLeft` | 扩展`.bubble`的结构类，会将箭头置于模块的左部。 |
| `bubbleHorizontalExt` | 和`.bubbleLeft`或`.bubbleRight`组合使用的类，可以将对话框箭头移动到左侧或右侧的底部。 |
| `bubbleVerticalExt` | 和`.bubbleTop`或`.bubbleBottom`组合使用的类，可以将对话框箭头移动到顶部或底部的右部。 |


## 文件（Files）

- talk.html
- /css/talk.css
- /css/talk_skins.css

Unless you are building a complex application or interactive site it is unlikely that you will need all of the code for the different positions of the talk-nub. Keep the ones you need to make the stylesheet even smaller.

除非正在构建一个复杂的应用程序或交互式网站，否则不太可能需要所有8种不同位置的对话框代码。记住，样式表的体积越小越好。


