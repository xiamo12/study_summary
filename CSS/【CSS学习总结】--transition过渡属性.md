[TOC]

------

#  一、transition的定义和语法

## 1. 定义

transition是CSS3中新增的一个属性，它是一个简写属性，用来显示过渡效果。可以把transition属性看成动画效果的一个实现。

## 2. 语法

transition属性的完整特性包括四种：

### transition-property

要设置过渡属性的属性名。例如：

```
transition-property: width
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

 表示为宽度设置过渡属性。

### transition-duration

过渡效果需要多少秒或者多少毫秒来完成。transition-duration的值必须要指定，否则过渡效果无法表示出来。

### transition-timing-function

指定transition效果的转速曲线。这个值用来描述当过渡效果在实现的时候，是以什么样的速度来实现的。

比如transition-timing-function：linear表示过渡效果以同样的速度开始直至结束；

transition-timing-function：ease表示慢速开始，然后变快，然后慢速结束；

### transition-delay

这个属性规定了transition开始的时间，表示在规定时间之后【s/ms】过渡效果才开始。

# 二、transition属性的使用

## transition+:hover伪元素

利用transition配合伪元素hover，可以做很多有意思的事情。比如模拟近大远小。

```css
.test{
	width: 100px;
	height: 100px;
	background: #333;
	margin: 100px auto;
	border-radius: 50%;
	box-shadow: 0px 0px 50px 20px rgba(255,255,0,0.9);
	transition: 0.5s linear;
}

.test:hover{
	width: 50px;
	height: 50px;
	box-shadow: 0px 0px 20px 10px rgba(255,255,0,0.9);
}
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

效果：

![img](https://img-blog.csdnimg.cn/20190814231323240.gif)

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

## transition+transform

用**transition+transform**也可以实现与上述效果类似的效果：

```css
.test{
	width: 100px;
	height: 100px;
	background: rgba(255,255,0,0.9);
	margin: 200px auto;
	border-radius: 50%;
	box-shadow: 0px 0px 50px 20px rgba(255,255,0,0.9);
	transition: 0.5s linear;
	transform: scale(1);
}

.test:hover{
	box-shadow: 0px 0px 40px 10px rgba(255,255,0,0.9);
	transform: scale(1.6);
}
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

![img](https://img-blog.csdnimg.cn/20190815091226653.gif)

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

这里提一下transform和transition的区别：transform属性是为了丰富DOM节点的变换形式；而transition操作了DOM节点样式的运动。

## transition+animation

写着写着发现可以配合动画属性**animation**玩，我们来模仿一下日落：

```css
.test{
	width: 100px;
	height: 100px;
	background: rgba(255,255,0,0.9);
	margin: 200px auto;
	border-radius: 50%;
	box-shadow: 0px 0px 50px 20px rgba(255,255,0,0.9);
	transition: 0.5s linear;
	position: relative;
	-webkit-animation: anim 2s linear;
	animation-fill-mode: forwards; /*使动画停留在结束的位置*/
}
.test:hover{
	width: 100px;
	height: 100px;
	box-shadow: 0px 0px 20px 10px rgba(255,255,0,0.9);
}
@keyframes anim{
	0% {
		left: 0;
		top: 0;
	}
	100%{
		left: 150px;
		top: 90px;
	}
}
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

这部分主要是animation的功劳:)

![img](https://img-blog.csdnimg.cn/20190815084148179.gif)

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)