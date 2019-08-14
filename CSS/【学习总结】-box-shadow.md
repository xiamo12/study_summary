今天在写一个点亮灯泡的小项目的时候，用到了box-shadow属性。感觉这个属性挺有意思的，索性专门整理一下。

[TOC]

------

# 一. box-shadow的定义和语法

1. **定义：**box-shadow是css3新增的一个属性。在W3School里，定义box-shadow是向框添加一个或者多个阴影的属性。
2. **语法**：box-shadow: h-shadow v-shadow blur spread color inset. 

- h-shadow: 阴影的水平位置
- v-shadow：阴影的垂直位置
- blur：阴影的模糊半径
- spread：阴影的半径
- color：阴影的颜色
- inset：将外部阴影改成内部阴影【outset反过来】

根据box-shadow的定义，我们可以为一个框设置一个阴影，也可以设置多个阴影。

当我们需要设置多个阴影时，中间需要将每个阴影用逗号隔开。

举个例子：

```css
/*html代码*/
<div class="test"></div>


/*对应的css代码*/
.test{
	width: 100px;
	height: 100px;
	background: yellow;
	margin: 100px auto;
	border-radius: 50%;
	box-shadow: 10px 10px 20px 10px rgba(255,255,0,0.5), -10px 10px 10px 10px rgba(255,255,255,0.5)
}
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

这里我们用border-radius属性设置了一个圆形，并且为这个圆形添加了一个浅黄色阴影和一个白色的阴影。

以第一个阴影：box-shadow: 10px 10px 20px 10px rgba(255,255,0,0.5)为例：

这段代码表示阴影的水平位置为右移10px；

垂直位置为下移10px；

第三个10px代表阴影的模糊程度blur，我们也将它设置成20px；

第四个10px是阴影半径的意思；最后一个规定了阴影的颜色为rgba(255,255,0,0.5)。

也就是说，我们为class为test的div元素添加了一个偏离框，并且向右距离为10px、向下距离为10px、模糊半径为10px、阴影半径为10px的浅黄色的阴影。

根据上面的CSS代码，我们看一下同时设置了两个阴影的效果：

![img](https://img-blog.csdnimg.cn/20190814172836969.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

为了更直白地观察到上述阴影设置的效果，我们将第二个阴影删除，只保留第一个阴影：

![img](https://img-blog.csdnimg.cn/20190814172532799.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

效果是不是还不错？

# 二. box-shadow属性值的详细解析

根据前面的语法规则，box-shadow可以有六个值。接下来我们来聊一聊box-shadow属性里的每个值都怎么用

## 1.  h-shadow【必需】

这个值代表的是阴影在***x轴上***的阴影位置。可以是负值。

当它为***正值***的时候表示向右位移一定的距离【出现在元素的***右边***】，***负值***表示向左位移【出现在元素的***左边***】。这个距离的单位可以是px、em或者rem；

需要注意的是：**h-shadow是必需的，不能省略！**

```
box-shadow: 10px 0px 10px rgba(0,0,0,0.9) /*阴影出现在元素的右侧*/

box-shadow: -10px 0px 10px rgba(0,0,0,0.9) /*阴影出现在元素的左侧*/
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

![img](https://img-blog.csdnimg.cn/20190814174829459.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)![img](https://img-blog.csdnimg.cn/2019081417492079.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

## 2.  v-shadow【必需】

这个值表示阴影在***y轴上***的位置。也可以是负值。

当***值为负***的时候表示向上偏移一定的距离【出现在元素的***上方***】；***值为正***的时候表示向下偏移一定的距离【出现的元素的下***方***】

```
box-shadow: 0px -20px 10px rgba(0,0,0,0.9)/*阴影出现在元素上方*/
box-shadow: 0px 20px 10px rgba(0,0,0,0.9)/*阴影出现在元素下方*/
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

![img](https://img-blog.csdnimg.cn/20190814175314858.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)![img](https://img-blog.csdnimg.cn/20190814175325253.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

## 3. blur【可选】

blur指的是阴影的模糊半径。这个值使得阴影部分的过渡看起来更柔和。我们可以试一试不同blur值对阴影效果的影响：

```
box-shadow: 10px 10px 5px rgba(0,0,0,0.9) /*blur值为5px*/
box-shadow: 10px 10px 10px rgba(0,0,0,0.9)/*blur值为10px*/
box-shadow: 10px 10px 15px rgba(0,0,0,0.9)/*blur值为15px*/
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

将blur值为5px、10px、15px 的效果图依次从左往右排列，可以看出来随着模糊半径数值的增大，阴影的模糊程度越高。

![img](https://img-blog.csdnimg.cn/2019081418005782.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)![img](https://img-blog.csdnimg.cn/20190814180105928.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)![img](https://img-blog.csdnimg.cn/20190814180124797.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

## 4. spread【可选】

spread表示的是阴影的半径。我在网上看到有人对spread和blur的区别发出疑问，其实很简单：blur用于描述模糊半径，它的值决定了阴影的模糊程度；而spread是表示阴影所占区域的大小，这是两个不同的概念。

我们来试试其他属性值相同的情况下，spread不同时阴影的表现：

```
box-shadow: 10px 10px 10px 5px rgba(0,0,0,0.9);/*阴影半径为5px*/
box-shadow: 10px 10px 10px 15px rgba(0,0,0,0.9);/*阴影半径为15px*/
box-shadow: 10px 10px 10px 25px rgba(0,0,0,0.9);/*阴影半径为25px*/
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

将spread的值为5px、15px、25px的效果图依次 从左向右排列，很明显阴影在逐渐变大

![img](https://img-blog.csdnimg.cn/20190814180936817.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)![img](https://img-blog.csdnimg.cn/20190814180944833.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)![img](https://img-blog.csdnimg.cn/20190814180957400.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

## 5. color【可选】

阴影的颜色可以用任何颜色单位来表示。当我们没有设置color值的时候，默认就是黑色。

```
box-shadow: 10px 10px 10px 5px rgba(0,0,0,0.9);/*黑色阴影，用rgba表示，透明度为0.9*/
box-shadow: 10px 10px 10px 5px rgb(255,0,0);/*红色阴影，用rgb表示*/
box-shadow: 10px 10px 10px 5px #afe;/*浅蓝色阴影，用十六进制颜色表示法*/
box-shadow: 10px 10px 10px 5px blue;/*蓝色阴影，用颜色单词表示*/
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

![img](https://img-blog.csdnimg.cn/20190814182319547.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)![img](https://img-blog.csdnimg.cn/20190814182345366.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)![img](https://img-blog.csdnimg.cn/20190814182353198.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)![img](https://img-blog.csdnimg.cn/20190814182400596.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

## 6. inset 【可选】

默认情况下，我们设置的阴影都是外部阴影，而这个属性值的作用是将外部阴影转换成内部阴影。

```
box-shadow: 10px 10px 10px 5px blue; /*默认为外部阴影*/
box-shadow: 10px 10px 10px 5px blue inset;/*将外部阴影切换为内部阴影*/
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

![img](https://img-blog.csdnimg.cn/20190814182842760.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)![img](https://img-blog.csdnimg.cn/20190814182845529.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW1vY3Nkbg==,size_16,color_FFFFFF,t_70)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

## 7. 一些有趣的实践 

了解了box-shadow之后，我们可以用来做一些有趣的事情。比如给阴影添加动画，对元素添加：hover伪元素，形成鼠标悬浮在元素上时，阴影扩大的效果 

```
.test{
	width: 100px;
	height: 100px;
	background: yellow;
	margin: 100px auto;
	border-radius: 50%;
	box-shadow: 0px 0px 10px 5px rgba(0,0,0,0.9);
	transform: scale(1);
	transition: box-shadow 0.6s, transform 0.5s;
}

.test:hover{
	width: 100px;
	height: 100px;
	background: yellow;
	margin: 100px auto;
	border-radius: 50%;
	box-shadow: 0px 0px 50px 15px rgba(0,0,0,0.9);
	transition: box-shadow 0.5s;
}
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

![img](https://img-blog.csdnimg.cn/20190814190501855.gif)

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

怎么样，box-shadow属性是不是挺有意思的？

------

好了，今天关于边框阴影box-shadow 属性的总结就写到这里了。鉴于刚刚做上面这个鼠标悬浮效果的时候用到了CSS3的另外两个新属性transition和transform，我打算下次来写一些这两个属性。

OVER！

感谢阅读。