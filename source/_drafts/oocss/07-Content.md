# 内容（Content）
[//]: # (上面部分是原翻译，下部分是我翻译的，只有一段翻译的是原翻译合适或者原翻译不全)

[原文](https://github.com/stubbornella/oocss/wiki/Content)

Some parts of content are ready for alpha testing, however, it isn't ready to be used in production projects. 

内容的一些部分已经准备好进行Alpha测试了，但是还没有准备好在生产项目中使用。

以下的一些内容已经准备好进行alpha测试了，但是还不适用于实际的生产项目中。

## 媒体对象（Media Object）
The media object allows you to have an image/flash or other fixed width media to the left or right with some content that describes it in the center. 

媒体对象允许您在左侧或右侧放置图像/flash动画或其他固定宽度的媒介，包含在中心位置的某些内容的描述。

媒体对象允许您在图像/Flash或其他固定宽度的媒介的左侧或右侧添加一些内容，以便将上述内容描述在中间的位置。

- Status: ready for alpha testing
- 状态：准备进行Alpha测试

### 基础类（Base Classes）

| Property      | Description                            |
| ------------- | ------------------------------------   |
| `media`         | Wrapper for the media object |
| `img`           | Child node of the media object. Generally a link, image, or flash wrapper. Will appear to the left of the `.bd.` Optional region.|
| `bd` | Main content area for the media object, can contain any other objects. Protected. Required region.|
| `imgExt` | Child node of the media object. Generally a link, image, or flash wrapper. Will appear to the right of the `.bd.` Optional region. |

| 属性      | 描述                            |
| ------------- | ------------------------------------   |
| media         | 媒体对象的包装器 |
| img           | 媒体对象的子节点。通常是链接，图像或动画的包装器。将出现在左边的 `.bd`。可选区域。|
| bd | 媒体对象的主要内容区域，可以包含任何其他对象。受保护的，必选区域。 |
| imgExt | 媒体对象的子节点。通常是链接，图像或动画的包装器。会出现在右边 `.bd`。可选区域。 |

| 属性      | 描述                            |
| ------------- | ------------------------------------   |
| `media`         | 媒体对象的容器 |
| `img`           | 媒体对象的子节点。通常是一个链接，图像或flash容器。通常会出现在`.bd.`左侧的可选区域。|
| `bd` | 媒体对象的主要内容区域，可以包含任何其他对象。它是默认存在的，并且是必选区域。 |
| `imgExt` | 媒体对象的子节点。通常是一个链接，图像或flash容器。通常会出现在 `.bd`.右侧的可选区域。 |


### HTML
```
<div class="media">
	<a href="http://twitter.com/stubbornella" class="img">
		<img src="http://a3.twimg.com/profile_images/72157651/tattoo_pink_bkg_square_mini.jpg" alt="Stubbornella" />
	</a>
	<div class="bd">
		<a href="http://twitter.com/stubbornella">@Stubbornella</a> <span class="detail">14 miniutes ago</span>
	</div>
</div>
```

## 数据表格（Data Table）

It can sometimes be convenient to be able to format a data table to align correctly for particular kinds of data (e.g. currency aligns right). Creating new classes for each kind of data can quickly bloat a file because ideally you want to be able to align the data with a class on the table, tr, td, or th, and have the class closest to the data win in case of conflict. This can be done, but it isn't how CSS automatically works, so to keep file size down, generic classes that support alignment can be used in conjunction with more semantic classes or microformats. 

有时可以很方便的格式化数据表，以便正确对齐特定类型的数据（例如货币对齐）。为每种数据创建新类可能会使文件迅速膨胀，因为您希望能够将数据与类关联，tr，td，th这些标签上设置类，是可以解决冲突的。这可以完成，但这不是CSS的自动工作方式，因此为了保持文件大小，支持对齐的通用类可以与多语义类或微格式一起使用。

它有时可以方便地格式化数据表格，使其可以正确的战术的某些数据（例如货币向右侧对齐）。为每种类型的数据创建新的类可能会使一个文件体积变得更大，因为理想情况下，您想在表格中的tr，td或th这些标签上的数据添加类属性。虽然这可以做单，但这不是CSS自动完成的，所以为了使文件体积缩小，我们可以使用通用的类来支持对齐，而这些通用类可以更多的结合语义化的类和微格式。

- Status: ready for alpha testing

- 状态：准备进行Alpha测试

### 基础类（Base Classes） 

| Property      | Description                            |
| ------------- | ------------------------------------   |
| `data`         | Div wrapper for the data table |
| `txtL`         | Aligns left, default alignment, can be applied to table, tr, td, or th. |
| `txtR` | Aligns right, can be applied to table, tr, td, or th. |
| `txtC` | Aligns center (horizontally), can be applied to table, tr, td, or th. |
| `txtT` | Aligns top, can be applied to table, tr, td, or th. |
| `txtB` | Aligns bottom, can be applied to table, tr, td, or th. |
| `txtM` | Aligns middle (vertically), can be applied to table, tr, td, or th. |


| 属性      | 描述                            |
| ------------- | ------------------------------------   |
| 数据   | 用Div包住数据表格 |
| `txtL` | 左对齐, 属于默认对齐方式, 可被用于：table, tr, td, 或 th。 |
| `txtR` | 右对齐, 可被用于：table, tr, td, 或 th。 |
| `txtC` | 居中对齐 (水平方向上), 可被用于：table, tr, td, 或 th。 |
| `txtT` | 上对齐, 可被用于：table, tr, td, 或 th。 |
| `txtB` | 底对齐, 可被用于：table, tr, td, 或 th。 |
| `txtM` | 居中对齐 (垂直方向上), 可被用于：table, tr, td, 或 th。 |

### HTML
```
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

## 文件（Files）

* /css/content.css
