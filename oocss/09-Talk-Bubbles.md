# 谈话框（Talk Bubbles）

[原文](https://github.com/stubbornella/oocss/wiki/Talk-Bubbles)

Talk bubbles were created to give context specific help, however they may be used for other purposes like blog comments, cartoon-style talk bubbles, etc. 

谈话框是为了给文章内容特定的帮助而创建的，但是它们也可以用于其他目的，如博客评论，卡通式谈话框等。

<a href="http://www.flickr.com/photos/nicole_hugo/3897449437/" title="Talk Bubbles by Stubbornella (aka Nicole), on Flickr"><img src="http://farm4.static.flickr.com/3506/3897449437_6b0fe48b29_o.png" width="322" height="196" alt="Talk Bubbles" /></a>

- No images required
- Secondary elements in place to allow for borders (just make the lower b a bit larger and set the border color)
- Easy to adapt the size of the arrow
- Compatible with border-radius generated rounded corners
- Base CSS objects are 1K
- IE6 uses page background color for the transparent bits because it doesn't support the color keyword "transparent"
- Allows eight different arrow positions

- 不需要图片
- 属于次要元素，允许使用边框（只会使得边框有点大，并可以设置边框的颜色）
- 容易适应光标箭头的大小
- 兼容边界半径生成的圆角
- 基本的CSS对象只有1K
- IE6使用页面背景颜色设置透明度，因为它不支持color关键字“transparent”
- 运行巴中不同的光标箭头位置

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
| `bubble` | 应用于mod容器，这是所有谈话框的基类。 如果您要改变指针的大小，请您编辑这个类（外边距和边框宽度应该是相等的）。 |
| `bubbleTop` | 扩展于`.bubble`的结构类，会将指针置于模块的顶部。|
| `bubbleRight` | 扩展于`.bubble`的结构类，会将指针置于模块的右部。 |
| `bubbleBottom` | 扩展于`.bubble`的结构类，会将指针置于模块的下部。 |
| `bubbleLeft` | 扩展于`.bubble`的结构类，会将指针置于模块的左部。 |
| `bubbleHorizontalExt` | 一个可以和`.bubbleLeft`或`.bubbleRight`结合使用的类，可以将谈话指针移动到左侧或右侧的底部。 |
| `bubbleVerticalExt` | 一个可以和`.bubbleTop`或`.bubbleBottom`结合使用的类，可以将谈话指针移动到顶部或底部的右部。 |


## 文件（Files）

- talk.html
- /css/talk.css
- /css/talk_skins.css

Unless you are building a complex application or interactive site it is unlikely that you will need all of the code for the different positions of the talk-nub. Keep the ones you need to make the stylesheet even smaller.

除非您正在构建一个复杂的应用程序或交互式网站，否则你不太可能需要所有不同位置的谈话框的代码。记住，保持你需要的样式表的体积更小一些。


