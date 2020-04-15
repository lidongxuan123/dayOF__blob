---
title: Visjs介绍
date: 2020-04-11 17:04:10
tags: Visjs介绍
categories: 
- topo图的使用方式
---

# 方法介绍
1. getScale()
    返回值：数字
    返回网络的规模。这可以是动画。这个比例就像一个百分比，1.0 = 100%。放大为> 1.0，缩小为< 0。比例不能小于或等于0。
2. getCenterCoordinates()
    返回值：数字
    返回屏幕中心的x和y坐标(在画布空间中)
3. getBoundingBox()
    返回值：对象
    为节点返回一个包围框，其中包含格式为:{top:Number,left:Number,right:Number,bottom:Number}的标签。这些值位于画布空间中。
4. getSelection()
    返回值：id数组
    返回一个具有所选节点id的数组。如果没有选择节点，则返回空数组。选择是无序的。
5. focusOnNode(nodeId, options)
    返回值：空
    该函数将视图移动到指定节点的中心。在可以定义动画属性的地方可以提交一个可选的options对象
    options: {
        scale: Number  放大到那个尺度，
        offset: {
            x: 
            y: 
        } 要偏移画布中心的位置(以像素为单位)，
        looked: boolean  如果为真，视图将一直锁定在这个节点上，直到完成另一个focusOnNode、mo否决、releaseNode或拖动
        animation: object || Boolean  来定义动画的细节。真是动画与默认设置，假不是动画。
        动画对象可以包括:
        duration: Number,  动画的持续时间以毫秒为单位
        easingFunction: string,  easingFunction:字符串 -动画的缓动功能，可用的有: 线性，easeInQuad, easeOutQuad, easeInQuad, easeInCubic, easeOutCubic, easeInOutCubic, easeInQuart, easeOutQuart, easeInOutQuart, easeInQuint, easeOutQuint, easeInOutQuint
    }
6. relaseNode()
    当锁定到一个节点时，这个函数再次释放它。如果由于focusOnNode锁定选项而没有将视图锁定到节点上，则什么也不会发生。
7. DOMtoCanvas(pos)
    此函数将DOM坐标转换为画布上的坐标。输入和输出的形式是{x:xpos,y:ypos}。DOM值是相对于网络容器的。
8. canvasToDOM(pos)
    此函数将画布坐标转换为DOM上的坐标。输入和输出的形式是{x:xpos,y:ypos}。DOM值是相对于网络容器的。
9. moveTo(options)
    此函数允许您以编程方式移动视图

10. on(event, callback)
    创建一个事件监听器。每次触发事件时都会调用回调函数。Avialable事件:选择。回调函数被调用为回调(属性)，其中属性是一个包含事件特定属性的对象。有关更多信息，请参见“事件”一节。
11. off(event, callback)
    删除以前通过函数on(event, callback)创建的事件监听器。有关更多信息，请参见“事件”一节。
12. destory()
    删除所有绑定并在网络之后进行清理。
13. redraw()
    重绘网络。当网页的布局改变时很有用
14. setData(data,[disableStart])
    加载数据。参数数据是一个包含节点、边和选项的对象。参数节点，边是一个数组。Options是一个名称-值映射，是可选的。参数disableStart是一个可选的布尔值，可以禁用模拟的开始，将在这个函数的末尾开始默认。
15. setOptions(options)
    设置网络选项。可用的选项在配置选项一节中进行了描述。
16. selectNodes(selection)   selectEdges(selection)
    选择节点。选择是一个包含要选择的节点id的数组。数组选择可以包含零个或多个id。示例用法:网络。selectNodes ([3,5]);将选择id为3和5的节点。highlisghEdges布尔值可用于自动选择连接到节点的边。
    选择边缘。选择是一个带有要选择的边的id的数组。数组选择可以包含零个或多个id。示例用法:网络。selectEdges ([3,5]);将选择id为3和5的边。
17. setSize(width, height)
    参数宽度和高度是字符串，包含用于显示的新大小。大小可以提供像素或百分比。
18. getPositons(ids)
    这将返回所有节点位置的对象。可以使用object[nodeId]访问数据。x和.y。您可以选择以字符串、数字或id数组的形式提供id。如果没有提供id或id数组，则返回所有位置。
19. storePositions
    当使用vis.DataSet将节点加载到网络中时，该方法将把所有节点的X和Y位置放入该数据集中。它还将包含具有正确值的allowedToMoveX和allowedToMoveY。如果您正在从数据库加载节点，并将其与数据集动态耦合，那么您可以使用它来稳定您的网络一次，然后通过数据集保存数据库中的位置，以便在下一次加载节点时，稳定将几乎是瞬时的。如果节点仍然在移动，而你使用的是动态平滑边缘(默认是打开的)，
20. zoomExtent()
    扩展网络，使所有节点都在中心视图中。您也可以为动画提供选项。这些选项可以是布尔值。当为真时，缩放是动画的，当为假则没有动画。或者，您可以提供一个对象
21. getSeed()
    根据位置算出一个字符串，把这个值放到layout里的randomSeed: "xxxx"当刷新的时候位置不变