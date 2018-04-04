# EaselJS Module(EaselJS 模块)

--------

The EaselJS Javascript library provides a retained graphics mode for canvas including a full hierarchical display list, a core interaction model, and helper classes to make working with 2D graphics in Canvas much easier. EaselJS provides straight forward solutions for working with rich graphics and interactivity with HTML5 Canvas...

EaselJS Javascript库为canvas提供了一个有所保留的图形模式，其中包括完整的分层的显示列表，核心交互模型和可以使在Canvas中处理2D图形更轻松的帮助类。 EaselJS为处理丰富的图形和与HTML5 Canvas交互提供了直接的解决方案...

### Getting Started(开始！)

To get started with Easel, create a Stage that wraps a CANVAS element, and add DisplayObject instances as children. EaselJS supports:

开始使用Easel时，我们创建了一个包装CANVAS元素的Stage，并添加DisplayObject实例作为子元素。其中EaselJS支持：

- Images using Bitmap
- Vector graphics using Shape and Graphics
- Animated bitmaps using SpriteSheet and Sprite
- Simple text instances using Text
- Containers that hold other DisplayObjects using Container
- Control HTML DOM elements using DOMElement

- 可以使用位图图像
- 矢量图形可以使用Shape和Graphics
- 动画位图可以使用SpriteSheet和Sprite
- 可以使用包含简单文本实例的Text
- 可以使用Container来包含其他DisplayObject的容器
- 可以使用DOMElement来控制HTML DOM元素

All display objects can be added to the stage as children, or drawn to a canvas directly.

所有展示性的对象都可以被当做子元素直接添加到舞台上，或者直接在canvas上绘制而成。

### User Interactions(用户交互)

All display objects on stage (except DOMElement) will dispatch events when interacted with using a mouse or touch. EaselJS supports hover, press, and release events, as well as an easy-to-use drag-and-drop model. Check out [MouseEvent](https://www.createjs.com/docs/easeljs/classes/MouseEvent.html) for more information.

所有舞台上的展示元素（除了DOM元素）都会在使用鼠标或触摸交互时触发事件。EaselJS支持悬停，按下和释放事件，以及一个方便使用的拖放模型。查看[MouseEvent](https://www.createjs.com/docs/easeljs/classes/MouseEvent.html)了解更多信息。

### Simple Example(简单的例子)

This example illustrates how to create and position a [Shape](https://www.createjs.com/docs/easeljs/classes/Shape.html) on the [Stage](https://www.createjs.com/docs/easeljs/classes/Shape.html) using EaselJS' drawing API.

这个例子阐述了如何在[Stage](https://www.createjs.com/docs/easeljs/classes/Shape.html)上使用EaselJS绘图的API创建并放置一个[Shape](https://www.createjs.com/docs/easeljs/classes/Shape.html)

```
//Create a stage by getting a reference to the canvas
stage = new createjs.Stage("demoCanvas");
//Create a Shape DisplayObject.
circle = new createjs.Shape();
circle.graphics.beginFill("red").drawCircle(0, 0, 40);
//Set position of Shape instance.
circle.x = circle.y = 50;
//Add Shape instance to stage display list.
stage.addChild(circle);
//Update stage will render next frame
stage.update();
```

### Simple Interaction Example(一个简单的交互例子)

```
displayObject.addEventListener("click", handleClick);
 function handleClick(event){
     // Click happenened
 }

 displayObject.addEventListener("mousedown", handlePress);
 function handlePress(event) {
     // A mouse press happened.
     // Listen for mouse move while the mouse is down:
     event.addEventListener("mousemove", handleMove);
 }
 function handleMove(event) {
     // Check out the DragAndDrop example in GitHub for more
 }

```

### Simple Animation Example(一个简单的动画例子)

This example moves the shape created in the previous demo across the screen.

这个例子将上一个demo中的创建shape移动出屏幕

```
//Update stage will render next frame
createjs.Ticker.addEventListener("tick", handleTick);

function handleTick() {
	//Circle will move 10 units to the right.
	circle.x += 10;
	//Will cause the circle to wrap back
	if (circle.x > stage.canvas.width) { circle.x = 0; }
	stage.update();
}
```

### Other Features(其他的特性)

EaselJS also has built in support for

- Canvas features such as [Shadow](https://www.createjs.com/docs/easeljs/classes/Shadow.html) and CompositeOperation
- [Ticker](https://www.createjs.com/docs/easeljs/classes/Ticker.html), a global heartbeat that objects can subscribe to
- Filters, including a provided [ColorMatrixFilter](https://www.createjs.com/docs/easeljs/classes/ColorMatrixFilter.html), [AlphaMaskFilter](https://www.createjs.com/docs/easeljs/classes/AlphaMaskFilter.html), [AlphaMapFilter](https://www.createjs.com/docs/easeljs/classes/AlphaMapFilter.html), and [BlurFilter](https://www.createjs.com/docs/easeljs/classes/BlurFilter.html). See [Filter](https://www.createjs.com/docs/easeljs/classes/Filter.html) for more information
- A [ButtonHelper](https://www.createjs.com/docs/easeljs/classes/ButtonHelper.html) utility, to easily create interactive buttons
- [SpriteSheetUtils](https://www.createjs.com/docs/easeljs/classes/SpriteSheetUtils.html) and a [SpriteSheetBuilder](https://www.createjs.com/docs/easeljs/classes/SpriteSheetBuilder.html) to help build and manage SpriteSheet functionality at run-time.


EaselJS也内置支持下列的内容：

- 像[Shadow](https://www.createjs.com/docs/easeljs/classes/Shadow.html)和CompositeOperation这样的Canvas特性
- [Ticker](https://www.createjs.com/docs/easeljs/classes/Ticker.html)，一个全局的心跳监测属性
- 过滤器，包括提供的[ColorMatrixFilter](https://www.createjs.com/docs/easeljs/classes/ColorMatrixFilter.html)，[AlphaMaskFilter](https://www.createjs.com/docs/easeljs/classes/AlphaMaskFilter.html)，[AlphaMapFilter](https://www.createjs.com/docs/easeljs/classes/AlphaMapFilter.html)和[BlurFilter](https://www.createjs.com/docs/easeljs/classes/BlurFilter.html)。 请参阅[过滤器](https://www.createjs.com/docs/easeljs/classes/Filter.html)了解更多信息
- 一个[ButtonHelper](https://www.createjs.com/docs/easeljs/classes/ButtonHelper.html)的实用程序，可以轻松创建交互式按钮
- [SpriteSheetUtils](https://www.createjs.com/docs/easeljs/classes/SpriteSheetUtils.html)和[SpriteSheetBuilder](https://www.createjs.com/docs/easeljs/classes/SpriteSheetBuilder.html)可帮助在运行时构建和管理SpriteSheet。

### Browser Support(浏览器支持)

All modern browsers that support Canvas will support EaselJS (http://caniuse.com/canvas). Browser performance may vary between platforms, for example, Android Canvas has poor hardware support, and is much slower on average than most other browsers.

所有的现代浏览器都支持可以使用EaselJS(http://caniuse.com/canvas)的Canvas。在不同的平台下浏览器的表现可能不同。例如，在Android下，Canvas在硬件上的支持并不好，并且相对于其他大多数浏览器的平均水平而言，它的运行速度令人捉急。
