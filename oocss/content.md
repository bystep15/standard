# Content 内容

Some parts of content are ready for alpha testing, however, it isn’t ready to be used in production projects.
内容的一些部分已经准备好进行Alpha测试了，但是还没有准备好在生产项目中使用。

## Media Object 媒体对象

The media object allows you to have an image/flash or other fixed width media to the left or right with some content that describes it in the center.
媒体对象允许您在左侧或右侧放置图像/flash动画或其他固定宽度的媒介，包含在中心位置的某些内容的描述。

* Status: ready for alpha testing
* 状态：准备进行Alpha测试

### Base Classes 基础类

| Property      | Description                            |
| ------------- | ------------------------------------   |
| media         | Wrapper for the media object |
| img           | Child node of the media object. Generally a link, image, or flash wrapper. Will appear to the left of the .bd. Optional region.|
| bd | Main content area for the media object, can contain any other objects. Protected. Required region.|
| imgExt | Child node of the media object. Generally a link, image, or flash wrapper. Will appear to the right of the .bd. Optional region. |


| 属性      | 描述                            |
| ------------- | ------------------------------------   |
| media         | 媒体对象的包装器 |
| img           | 媒体对象的子节点。通常是链接，图像或动画的包装器。将出现在左边的 `.bd`。可选区域。|
| bd | 媒体对象的主要内容区域，可以包含任何其他对象。受保护的，必选区域。 |
| imgExt | 媒体对象的子节点。通常是链接，图像或动画的包装器。会出现在右边 `.bd`。可选区域。 |



### HTML 代码

```html
<div class="media">
	<a href="http://twitter.com/stubbornella" class="img">
		<img src="http://a3.twimg.com/profile_images/72157651/tattoo_pink_bkg_square_mini.jpg" alt="Stubbornella" />
	</a>
	<div class="bd">
		<a href="http://twitter.com/stubbornella">@Stubbornella</a> <span class="detail">14 miniutes ago</span>
	</div>
</div>
```

## Data Table 数据表格

It can sometimes be convenient to be able to format a data table to align correctly for particular kinds of data (e.g. currency aligns right). Creating new classes for each kind of data can quickly bloat a file because ideally you want to be able to align the data with a class on the table, tr, td, or th, and have the class closest to the data win in case of conflict. This can be done, but it isn’t how CSS automatically works, so to keep file size down, generic classes that support alignment can be used in conjunction with more semantic classes or microformats.
有时可以很方便的格式化数据表，以便正确对齐特定类型的数据（例如货币对齐）。为每种数据创建新类可能会使文件迅速膨胀，因为您希望能够将数据与类关联，tr，td，th这些标签上设置类，是可以解决冲突的。这可以完成，但这不是CSS的自动工作方式，因此为了保持文件大小，支持对齐的通用类可以与多语义类或微格式一起使用。

Status: ready for alpha testing
状态：准备进行Alpha测试

### Base Classes 基础类

| Property      | Description                            |
| ------------- | ------------------------------------   |
| data         | Div wrapper for the data table |
| txtL         | Aligns left, default alignment, can be applied to table, tr, td, or th. |
| txtR | Aligns right, can be applied to table, tr, td, or th. |
| txtC | Aligns center (horizontally), can be applied to table, tr, td, or th. |
| txtT | Aligns top, can be applied to table, tr, td, or th. |
| txtB | Aligns bottom, can be applied to table, tr, td, or th. |
| txtM | Aligns middle (vertically), can be applied to table, tr, td, or th. |


| 属性      | 描述                            |
| ------------- | ------------------------------------   |
| 数据         | 用Div包装数据表格 |
| txtL         | 左对齐, 默认对齐方式, 可被用于：table, tr, td, 或 th。 |
| txtR | 右对齐, 可被用于：table, tr, td, 或 th。 |
| txtC | 居中对齐 (水平的), 可被用于：table, tr, td, 或 th。 |
| txtT | 上对齐, 可被用于：table, tr, td, 或 th。 |
| txtB | 底对齐, 可被用于：table, tr, td, 或 th。 |
| txtM | 居中对齐 (垂直), 可被用于：table, tr, td, 或 th。 |

### HTML 代码

```html
<div class="data">
  <table class="txtC"><!--table alignment set to center -->
    <tr class="odd txtL">
      <th scope="row" class="txtR">Right aligned</th>
      <td>Left aligned</td>
    </tr>
    <tr class="even">
      <th scope="row">center aligned</th>
      <td>center aligned</td>
    </tr>
  </table>
</div>
```

### Files 文件
    
* /css/content.css