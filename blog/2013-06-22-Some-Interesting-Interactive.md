一些有意思的交互设计
===

### 1. 网易邮箱
**当用户在很短的时间内三次点击“收信”按钮之后，如果还没有收到新邮件，系统提示用户注意查看“垃圾邮件”。**  
当用户做出这样的动作时，基本都是用户被其他系统提示给他发送了一封邮件，然后用户急于查看邮件内容。如果该邮箱启动了垃圾邮件过滤功能，那么在多次刷新无果的情况下，就有可能是被当做垃圾邮件处理了，所以给出用户一种提示。这是几年前我注意到的交互行为，但是现在消失了。不知道是网易对自己的垃圾邮件判断准确率得到了大幅提高，还是其他原因，就不得而知了。  

### 2. 隐藏的菜单
在一些系统中，受到设备尺寸的限制或者是设计上的权衡，最后将菜单隐藏或者最小化处理。那么怎么才能告诉用户这里有菜单呢？有种做法在系统启动时，将执行**菜单从隐藏渐变到完全显示再渐变到隐藏**这样一个动画效果，以提示用户这里有个菜单，可以点击（或滑动）附近区域来显示菜单。  
这样也有一个问题，每次启动系统或者页面刷新时都会执行这样的动画会对用户造成一定骚扰。首先就是动画执行要快，不要影响用户的正常操作，然后就是当用户第一次弹出菜单以后，我们就认为用户学会了如何弹出菜单，以后就不再显示该动画效果。  
为什么会想到这样一个案例呢，是因为前几天午饭时，一个同事谈起他的新手机，底部Back，Home，Settings等菜单突然找不到了，重启机器也不会出现。然后上网搜索才知道是被不小心手指下滑隐藏了菜单，需要手指上滑来显示菜单。试想如果在用户重启以后会有上述的动画效果，或许能够提示用户。

### 3. 鲸鱼岛的冬天
（摘自程序员杂志201209 P71）
将游戏首页加上模糊处理，使它看起来像是玻璃上结了一层水雾。小朋友都会很自然的去擦，从而获得清晰的页面。据说很多小朋友都把整个页面擦干净才开始游戏。  
ABCKit等知名应用的开发者Karina Ibarra在Designing Apps For Kids一文中提出了儿童应用的设计要点：简短的启动画面（儿童缺乏耐心）、首页的设计（低龄儿童难以被其吸引）、应用相关设置简单（防止儿童误操作）、从大处着眼（易于识别）、任务机制简单（易用性原则）以及随时的赞美和鼓励。  
孩子如果想重启或者恢复一个游戏，故事或者活动时，他们不会按返回键来恢复游戏或者返回主页，大多数孩子会直接按下iPad或iPhone的Home键，先退出游戏，再重新开始游戏。