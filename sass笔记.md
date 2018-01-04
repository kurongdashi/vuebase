# sass、scss
## 安装ruby才能，安装scss
1. .sass是旧版语法，没有大括号和分号，而scss是现在语法使用和css类似
   所以文件命名用.scss后缀，否则无法编译


## 1、变量声明使用$
``` 
# 定义
$color:#e92322;
$color2:#efefef;

# 变量作用域在{}内定义的，只能在{}内使用
#app{
  $color1:#fefefe;

}


```

## 2  &符号，在嵌套中代表父级选择器

``` 
#app{
  a{
    color:$color;
      // 此处的& 代表 #app a
      &:hover{
        color: $color2;
      }
   }
}

>,+ ,~等css选择器通用适用于sass
```
## 前缀缩略
``` 
# 多个前缀名相同的属性例如border-xxx,background-xxx,使用 border:{ 分类属性}
#app{
  border:{
    style:solid;
    width:1px;
    color: $color2;
  }

}
```

##  导入其他sass文件

``` 
# 导入
@import 'a.sass'

# sass允许在选择器中使用@import
#app{
@import "_a.sass";
}

```
## 注释
1. 在sass中// 双斜线注释，在生成css文件中出现

2. /**/ 注释会出现在生产的css文件中




## 5、 混合器@mixin，混合器表示的是一段样式
1. 样式混合器
``` 
# 定义混合器 @mixin
@mixin hunhe{
padding:10px;
  color: #e4b9b9;
  font:{
    size:18px;
      family:'micrsoft YeHei';
    }
}


# 使用混合器@include
#app{
@include hunhe;

}

```
2. 函数混合器

``` 
# 定义函数混合器
@mixin a-style($color,$hover,$size:14px){

  color:$color;
    &:hover{ color:$hover};
  font-size: $size;
}


// 使用 @include
a{
  @include a-style($color:red,$hover:blue,$size:14px);
}
```


##  6、sass的继承
``` 
# 定义一段
.err{
  border: 1px solid red;
  background-color: #fdd;
}

# 继承上面的样式  @extend

.seriousError {
  //所有根.err相关的选择器都会继承
  @extend .error;
  border-width: 3px;

}

```

//(1)选择器继承@extends selector,



