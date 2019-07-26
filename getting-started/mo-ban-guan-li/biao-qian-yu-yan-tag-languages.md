# 标签语言\(Tag Languages\)

## 介绍

在上面的文档中，我们介绍了许多定义的标签语法，我们的模板管理系统对页面文件的模板语法是基于[**Twig**](https://twig.symfony.com/doc/2.x/)来实现的，您可以使用Twig官方的模板语法，同时也可以使用我们在其基础上扩展的一些方法，标签和过滤方法等。

## 用法

### 变量\(Variables\)

在模板文件中我们通过双括号加变量名来输出变量的值

```text
{{ variable }} // 输出变量值
{{ isAjax ? 'Yes' : 'No' }} // 根据变量值进行条件判断
{{ 'Your name: ' ~ name }}  // 拼接字符串
```

### 标签\(Tags\)

标签有更强大的功能，我们使用 {%  %} 包裹起来，例如前面文档有写出来的

```text
{% style %}
{% page %}
```

我们通过标签实现逻辑判断

```text
{% if list.key < 5 %}
    {{list.info}}
{% else %}
    ...
{% endif %}
```

通过set标签我们能通过模板进行变量赋值

```text
{% set company="CMSTop" %} // 定义

{{ company }} // 使用
```

### 过滤器\(Filters\)

通过过滤器我们可以对已有的变量值进行加工后再输出，基本语法为

{{ variables\|filter }}

例如

```markup
{% set sizes = {
    xs: 34,
    s:  36,
    m:  38,
    l:  40,
    xl: 42,
} %}

{{sizes|length}}   // 输出5
{{ 'Hello World'|upper|replace({'WORLD': 'SITUOYUN'}) }} // 输出 HELLO SITUOYUN 
{{sizes|join('|')}}  // 输出 34|36|38|40|42
```

更多Filter 请参见[**Twig**](https://twig.symfony.com/doc/2.x/)官网

### 函数\(Functions\)

函数能为我们提供定制化的输出，基本用法为

```text
{{ function() }} // 无参数
{{ dump(variable) }} // 带参数
```

### 模板变量值获取流程

在本系统中，使用Twig的模板语法`{{ foo.bar }}`来获取变量值，对对象foo来说，访问bar的值会按下面的顺序来获取

1. 如果foo是一个数组并且bar是其中的一个元素，就返回这个元素的值
2. 如果不满足上面的条件，如果foo是一个对象并且bar是它的一个可以访问的属性，就返回这个属性
3. 如果不满足上面的条件，如果foo是一个对象并且bar是它的一个可以访问的方法，就返回这个方法执行后返回的值
4. 如果不满足上面的条件，如果foo是一个对象并且getBar是它的一个可以访问的方法，就返回这个方法执行后返回的值
5. 如果不满足上面的条件，如果foo是一个对象并且isBar是它的一个可以访问的方法，就返回这个方法执行后返回的值
6. 如果不满足上面的条件，就返回`null`

### 暂不支持的Twig特性

本系统暂不支持Twig的一些特性，但是有替代的方法能实现同样的功能，如下

| 标签 | 替代的方案 |
| :--- | :--- |
| `{% extend %}` | 使用布局文件或者`{% placeholder %}` |
| `{% include %}` | 使用 `{% partial %}` 或者 `{% content %}` |



