title: 07、内容（Content）
categories: [理论, css, oocss]
tags: [理论, css, oocss]
date: 2018/06/27 10:30:00
---

[原文](https://github.com/stubbornella/oocss/wiki/Content)
[示例](http://oocss.org/library.html)

Some parts of content are ready for alpha testing, however, it isn't ready to be used in production projects. 

内容的一些部分已经准备好进行Alpha测试了，但是还没有准备好在生产项目中使用。

## 媒体对象（Media Object）
The media object allows you to have an image/flash or other fixed width media to the left or right with some content that describes it in the center. 

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
| `media` | 媒体对象的包裹容器 |
| `img` | 媒体对象的子节点，链接，图像或flash包裹容器。通常在左侧的`.bd`区域，可选区域。|
| `bd` | 媒体对象的主要内容区域，可以包含任何其他对象。受保护，必选区域。 |
| `imgExt` | 媒体对象的子节点，链接，图像或flash包裹容器。通常在右侧的`.bd`区域，可选区域。 |


### HTML
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

## 数据表格（Data Table）

It can sometimes be convenient to be able to format a data table to align correctly for particular kinds of data (e.g. currency aligns right). Creating new classes for each kind of data can quickly bloat a file because ideally you want to be able to align the data with a class on the table, tr, td, or th, and have the class closest to the data win in case of conflict. This can be done, but it isn't how CSS automatically works, so to keep file size down, generic classes that support alignment can be used in conjunction with more semantic classes or microformats. 

有时需要方便地格式化数据表格，以便正确对齐特定类型的数据（例如货币右侧对齐）。为每种类型的数据创建新类可能会使文件体积迅速膨胀，理想情况下，在表格中的tr，td或th标签上设置类属性，数据自动与其对齐。虽然可以这样做做，但这不是CSS的方式，所以为了使文件体积缩小，支持对齐的通用类可以与多语义类或微格式一起使用。

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
| `data`| 数据表格的Div包裹容器 |
| `txtL` | 左对齐, 属于默认对齐方式, 可被用于：table, tr, td, 或 th。 |
| `txtR` | 右对齐, 可被用于：table, tr, td, 或 th。 |
| `txtC` | 居中对齐 (水平方向上), 可被用于：table, tr, td, 或 th。 |
| `txtT` | 上对齐, 可被用于：table, tr, td, 或 th。 |
| `txtB` | 底对齐, 可被用于：table, tr, td, 或 th。 |
| `txtM` | 居中对齐 (垂直方向上), 可被用于：table, tr, td, 或 th。 |

### HTML
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

## 文件（Files）

* /css/content.css
