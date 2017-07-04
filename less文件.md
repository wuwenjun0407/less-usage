# less文件

### 简介
>less 也是来写样式的跟css一样都是实现样式的写法，只不过语法不同，它涵盖了一些JS的思想

### 变量
>在JS中声明变量有两种 var function
>在less中变量前面加上@符号
```
@(less)color:#ff6700;
.box1{
color: @color;
}
```
#### 还可以以变量的名定义为变量
```
//@word:"I love you";
//@c:#ff5700;
//@var:"word";//定义了一个变量var赋值为另一个变量名word
//@col:"c";//定义了一个变量var赋值为一个变量名c
//#p1:after{
//  content: @@var;//@（@var）->@word ->"I love you"
//}

```
#### 混合类
```
//.class{
//  font-size: 20px;
//  width: 200px;
//  height: 50px;
//  border: 1px solid red;
//}
//.box1{
//  .class;
//  background-color: #0000FF;
//}
```

#### 匹配模式和引导表达式
```
//.min(drak,@color){
//  color: darken(@color,20%);//darken:将当前颜色加深20%
//}
//.min(light,@color){
//  color: lighten(@color,20%);//lighten:将当前颜色变浅20%
//}
//.min(@_,@color){
//  display: block;
//}
//@switch1:drak;
//@switch2:light;
//@_,接受任何值，你传什么都会执行
```

####	带参数混合
>在less中可以像JS函数一样定义一个带参数的属性集合
```
//.border{
//  
//}
//.radius(@rad){
//  border-radius: @rad;
//  -webkit-border-radius: @rad;
//}
//.box1{
//  .radius(10px)
//}

```
#### 嵌套规则
>1.直接嵌套表示的是后代关系
>2.如果想表达的是当前的选择器加一个&来表示（一般都是元素伪类用的比较多）
```
//.wh(@w:100px,@h:100px){
//  width: @w;
//  height: @h;
//}
//div{
//  .wh();
//  p{
//      .wh(100px,20px);
//  }
//}
//
//.box{
//  .wh();
//  &:hover{
//      background-color: darkblue;
//  }
//}
```
#### 计算功能：任何颜色，变量都可以参与运算
```
//@base:5%;
//@filter:@base *2;//10%
//@other: @base *4 + @filter//30%
//
//.box{
//  color: #FFFF00;
//  background-color:@filter+#111;
//  height: 100%/2 + @other;
//}

```
#### 命名空间
```
#box1{
    .p1{
        width: 100px;
        height: 30px;
        border: 1px solid red;
        &:hover{
            color: #FF0000;
        }
    }
}
p2{
    color: #ccc;
    #box1>.p1
}
```
>
```
import"reset";
@import(reference)"public";
//@import使用他来导入外部文件
//@import(once):只包含文件一次
//@import(multiple):包含文件多次
//@import(reference):导入外部样式，但是不添加导入的样式到编译中
//@import(inline):在输出中包含源文件但不加工他
//@import(less):将文件作为less文件对象，不管文件扩展名是什么
//@import(css):将文件作为css文件对象，不管文件扩展名是什么
```