# 标签\(Tags\)

## {% page %}

此标签会返回当前页面解析完成的html数据，我们一般在layout的文件中应用，这样就能将页面的数据注入到layout的文件中，整合成一个完整的页面结构。

基本用法

```text
description="example layout"
==
<html>
    <head>
        {% placeholder head %}
    </head>
    <body>
        {% page %}
        ...

description="example page"
==
{% put head %}
    <meta name="foo" content="bar">
{% endput %}

<p>My content.</p>
```

最后返回的数据为

```text
<html>
    <head>
        <meta name="foo" content="bar">
    </head>
    <body>
        <p>My content.</p>
        ...
```

## {% partial %}

引入一个复用的部件，基本用法

```text
{% partial "footer" %}
{% partial "sidebar/menu" %}

// 也可以
{% set tabName = "profile" %}
{% partial tabName %}
```

### 传递参数

```text
{% partial "location" city="Vancouver" country="Canada" %}

<p>Country: {{ country }}, city: {{ city }}.</p>
```

### 检查部件是否存在

```text
{% set cardPartial = 'my-cards/' ~ cardCode %}

{% if partial(cardPartial) %}
    {% partial cardPartial %}
{% else %}
    <p>Card not found!</p>
{% endif %}
```

## {% content %}

内容标签能显示htm,txt,markdown格式的文档，基本用法如下

```text
{% content "contacts.htm" %}
{% content "contacts.md" %}  // markdown的内容会被转换成html的文本格式。
{% content "contacts.txt" %}
```

### 传递参数

```markup
{% content "location.htm" city="Vancouver" country="Canada" %}
<p>Country: {country}, city: {city}.</p>
```

```markup
{% content "welcome.htm" likes=[
    {name:'Dogs'},
    {name:'Fishing'},
    {name:'Golf'}
] %}

<ul>
    {likes}
        <li>{name}</li>
    {/likes}
</ul>
```

{% hint style="warning" %}
注意内容标签中，使用参数的方法是单大括号，和page,partial,layout的用法不同
{% endhint %}

## {% component %}

此标签会返回应用在页面组件的html解析后的数据，基本用法为

```text
{% component "posts" %}
```

### 参数传递

```text
{% component "posts" postsPerPage="5" %}
```

## {% placeholder %}

此标签相当于把模板中的一部分内容的控制权提供了出来，方便每个页面进行个性化编辑。

