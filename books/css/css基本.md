
# css

## css 基本

### css 基本的问题

问题： css选择器有哪些

问题： css选择器权重

问题： 盒模型

问题： 外边距塌陷

问题：布局方案

问题： BFC

问题： flex-box

问题： grid布局

问题： grid布局 项目属性

问题： 定位与层叠上下文

问题： 创建层叠上下文的方式

问题： 媒体查询


### css 基本的详情

##### 问题： css选择器有哪些

基本选择器：元素、类、ID、通配符

组合选择器：后代（空格）、子代（>）、相邻兄弟（+）、通用兄弟(~)

属性选择器 [attr] [attr=value] [attr^=val](前缀) [attr$=val](后缀) [attr*=val](子串) [attr~val](单词)

伪类 状态类 :hover,active,focus-visible,checked,disabled,target(跳转被激活的样式);结构类 :first-child/last-child,nth-child(odd)/nth-of-type(xx)(同类型的元素)，empty,root(指\<html\>);组合逻辑 :not(xx),is(h1,h2),where(nav),has(img) (父选子)

伪元素 ::before，after,first-line,first-letter,marker,selection,part,slotted,

##### 问题： css选择器权重

inline style --- 1000, #id --- 100, .class/[attr]/:pseudo-class --- 10, element/::pseudo-element --- 1,*,组合符，逗号 0, !import --- 最高 :is() --- 内部最强，:whre --- 权重为0

##### 问题： 盒模型

标准盒模型（content-box） Vs IE盒模型(border-box)，对于一个元素来说涉及到布局的css属性有四个margin，border，width，padding，标准盒模型元素的实际宽度是width + padding + border,内容尺寸就是width，而IE盒模型实际宽度就是width，内容尺寸是width - border - padding。 推荐使用IE盒模型，易于布局，更直观，现代框架常用


##### 问题： 外边距塌陷

css布局中，垂直外边距会发生塌陷，即相邻的块级元素之间的上下外边距不会简单的相加。而是会合并成为两个两者最大值的外边距。包括，1.两个兄弟元素间的外边距，2.父元素与首/末元素的外边距，3.空元素（无内容，无边框和内边距）

何时不会发生塌陷？1.有边框和内边距，2.浮动元素或清除浮动，3.设置了overflow(除visible外)，4.非块级布局，


##### 问题：布局方案

传统布局方案 `display: block/inline/inline-block`, line-box, BFC  

浮动

flexbox

grid

##### 问题： BFC

BFC (Block Formatting Context) 是 CSS 中的一个概念，它定义了一个独立的渲染区域，在这个区域内，元素的布局不会受到外部元素的影响，也不会影响外部元素的布局。BFC 在解决一些常见的布局问题时非常有用，例如清除浮动、防止垂直外边距重叠等。

BFC 的特性 1. 内部的Box会在垂直方向，一个接一个的放置。 2. Box垂直方向的距离由margin决定，属于同一个BFC的两个相邻的margin会发生重叠 3. 每个元素的margin box的左边，与包含border box的左边相接触 4. BFC区域不会与float box重叠 5. BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。 6. 计算BFC的高度时，浮动元素也参与计算

触发 满足任意条件即可触发 - body 根元素: - 浮动元素,float不为none - overflow 除了visible 以外的值 hidden auto scroll - display为inline-block table-cells flex table-caption - 绝对定位 position absolute fixed


##### 问题： flex-box

flex是一种布局方式，有两个概念，flex-container（flex容器）和flex-item（flex单元），flex-container是外层元素，flex-item是在flex-container内部的元素，通过一些属性来控制布局：

**flex-container**的主轴和交叉轴，主轴和交叉轴上都有属性控制布局方式，内部元素沿着主轴方向排列

flex-direction: 属性来控制主轴的方向，主轴确定了交叉轴也就确定了。包括row,row-reverse,column,column-reverse,默认是是row，表示以水平方向作为主轴，column表示以竖直方向作为主轴。加上reverse表示相反的方向作为主轴，主轴的概念就类似于一个矢量单位，带有方向的，row表示水平向右，row-reverse表示水平向左，column表示竖直向下，column-reverse表示竖直向上。

justify-content: 主轴上的对齐方式，flex-start,从主轴开始处排列，flex-end: 从主轴末尾处排列，space-around:每个元素平均分配剩下的空间，space-between: 两端的元素与容器紧挨着，剩下的元素平均分配剩余空间

align-items: 交叉轴的对齐方式，与主轴相同

algin-content: 多行的对齐方式

flex-wrap: 换行方式，nowrap不换行 wrap换行

flex-flow: flex-direction flex-wrap;的组合

**flex-item** flex的单元，控制自身在flex容器中的表现

flex-shrink: 收缩规则，0表示不缩小，1表示随着空间减少而缩小，只能是number，尽在元素的默认大小大于容器元素的尺寸是发生

flex-grow: 主尺寸flex的增长系数，初始0，1表示占据剩余的空间，0表示不放大

剩余空间是 flex 容器的大小减去所有 flex 项的大小加起来的大小。如果所有的兄弟项目都有相同的 flex-grow 系数，那么所有的项目将剩余空间按相同比例分配，否则将根据不同的 flex-grow 定义的比例进行分配 inherit initial unset revert

flex-basis: flex-basis 指定了 flex 元素在主轴方向上的初始大小。如果不使用 box-sizing 改变盒模型的话，那么这个属性就决定了 flex 元素的内容盒（content-box）的尺寸。

fill max-content min-content fit-content content 有兼容性问题

当一个元素同时被设置了 flex-basis (除值为 auto 外) 和 width (或者在 flex-direction: column 情况下设置了height) , flex-basis 具有更高的优先级。

order：显示顺序

algin-self: 自身在交叉轴上的排列方式，

问题： 常见的布局使用方式

flex: flex-grow flex-shrink flex-basis

##### 问题： grid布局

一句话先导：当 Flexbox 已经让“一维”排列（横 或 纵）变得轻松，Grid 则把布局能力扩展到真正的 二维网格。它能一次性描述整张页面/组件的行列轨道，让视觉与代码一一对应，维护成本直线下降。

网格容器 (grid container)	设置 display:grid/inline-grid 的元素,项目单元是指在容器的一级子元素;轨道 (track)	行或列，宽高由 grid-template-rows/columns 定义; 网格线 (grid line)	轨道之间的分隔线，编号从 1 开始，可自定义名字; 网格区域 (grid area)	多个单元格合并成的矩形，可用名字引用; 显式 / 隐式网格	前者由 grid-template-* 声明，后者由自动放置算法扩展

display:grid/inlie-grid开启grid容器，grid-template-coloums定义每一列的宽度，grid-template-rows定义每一行的高度,可以使用绝对单位（px,em），也可以是使用百分比;**repeat**,repeat(3,33%);repeat(2, 100px 20px 80px);**auto-fill**表示自动填充。单元大小是固定的，但是容器大小不是固定的。除了auto-fill，还有一个关键字auto-fit，两者的行为基本是相同的。只有当容器足够宽，可以在一行容纳所有单元格，并且单元格宽度不固定的时候，才会有行为差异：auto-fill会用空格子填满剩余宽度，auto-fit则会尽量扩大单元格的宽度。**fr关键字**（fraction 的缩写，意为"片段"）,如果两列的宽度分别为1fr和2fr，就表示后者是前者的两倍。fr可以与绝对长度的单位结合使用，这时会非常方便。  grid-template-columns: 150px 1fr 2fr;上面代码表示，第一列的宽度为150像素，第二列的宽度是第三列的一半。**minmax**,minmax()函数产生一个长度范围，表示长度就在这个范围之中。它接受两个参数，分别为最小值和最大值。grid-template-columns: 1fr 1fr minmax(100px, 1fr);上面代码中，minmax(100px, 1fr)表示列宽不小于100px，不大于1fr。**auto**,auto关键字表示由浏览器自己决定长度。**网格线的名称**grid-template-columns属性和grid-template-rows属性里面，还可以使用方括号，指定每一根网格线的名字，方便以后的引用。  grid-template-columns: [c1] 100px [c2] 100px [c3] auto [c4];网格布局允许同一根线有多个名字，比如[fifth-line row-5]。

gap: 列间距 行间距; 用来这是行间距和列间距

网格布局允许指定"区域"（area），一个区域由单个或多个单元格组成。grid-template-areas属性用于定义区域  grid-template-areas: 'a b c' 'd e f' 'g h i';。grid-template-areas: 'a a a' 'b b b' 'c c c'; grid-template-areas: "header header header" "main main sidebar" "footer footer footer";注意，区域的命名会影响到网格线。每个区域的起始网格线，会自动命名为区域名-start，终止网格线自动命名为区域名-end。
比如，区域名为header，则起始位置的水平网格线和垂直网格线叫做header-start，终止位置的水平网格线和垂直网格线叫做header-end。

grid-auto-flow,防止顺序，row，column; row-dense,col-dense

justify-items 属性， align-items 属性， place-items (\<align-items\> \<justify-items\>) 属性 start：对齐单元格的起始边缘。 end：对齐单元格的结束边缘。 center：单元格内部居中。 stretch：拉伸，占满单元格的整个宽度（默认值）。

justify-content 属性， align-content 属性， place-content 属性 start,end,center,stretch,space-between,spcace-around,space-evenly（平分间隔）

grid-auto-columns 属性， grid-auto-rows 属性 grid-auto-columns属性和grid-auto-rows属性用来设置，浏览器自动创建的多余网格的列宽和行高。它们的写法与grid-template-columns和grid-template-rows完全相同。如果不指定这两个属性，浏览器完全根据单元格内容的大小，决定新增网格的列宽和行高。

grid-template 属性， grid 属性 grid-template属性是grid-template-columns、grid-template-rows和grid-template-areas这三个属性的合并简写形式。 grid属性是grid-template-rows、grid-template-columns、grid-template-areas、 grid-auto-rows、grid-auto-columns、grid-auto-flow这六个属性的合并简写形式。 从易读易写的角度考虑，还是建议不要合并属性，所以这里就不详细介绍这两个属性了。

##### 问题： grid布局 项目属性

grid-column-start 属性， grid-column-end 属性， grid-row-start 属性， grid-row-end 属性  这四个属性的值还可以使用span关键字，表示"跨越"，即左右边框（上下边框）之间跨越多少个网格。

grid-column 属性， grid-row 属性 grid-column属性是grid-column-start和grid-column-end的合并简写形式，grid-row属性是grid-row-start属性和grid-row-end的合并简写形式。

grid-area属性指定项目放在哪一个区域。

grid-area属性还可用作grid-row-start、grid-column-start、grid-row-end、grid-column-end的合并简写形式，直接指定项目的位置。

justify-self 属性， align-self 属性， place-self 属性


##### 问题： 定位与层叠上下文

position: static | relative | absolute | fixed | sticky

##### 问题： 创建层叠上下文的方式

定位; opacity<1; transform / filter / perspective / backdrop-filter;  mix-blend-mode ≠ normal; isolation: isolate; will-change 包含以上任意属性; @layer 里的根规则（层叠级别控制）; 对于 Flex/Grid，容器若 z-index: auto 亦会成栈

##### 问题： 媒体查询

@media <媒体类型> [and | not | only] (<条件1>) [and (<条件2>)] { /* 满足所有条件时才执行 */ } 媒体类型：all | screen | print | speech（90 %以上场景可省略，等同于 all）,逻辑关键字： and——并且 not——取反 only——防旧浏览器把整个查询当作真（极少再用）。条件＝媒体特性（media features），如 width、hover、prefers-color-scheme 等。

尺寸断点， /* 设备宽度在 768 – 1023 px 之间 */ @media (min-width: 768px) and (max-width: 1023px) { … } 

CSS Media Queries Level 4 允许“比较运算符”： @media (768px <= width <= 1023px) { … } @media (width > 1200px)          { … }   /* 仅超宽屏 */