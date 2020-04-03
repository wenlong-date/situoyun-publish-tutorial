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

此标签相当于把模板中的一部分内容的控制权提供了出来，方便每个页面进行个性化编辑，一般用在布局中占位，然后在具体引用布局的文件中设置占位的内容。例如下面

```markup
// 声明占位符name
{% placeholder name %}

// 定义占位符name的具体内容
{% put name %}
    <p>Place this text in the name placeholder</p>
{% endput %}
```

### 设置默认输出内容

在布局中我们可以定义placeholder 标签默认输出的内容，如下例子

```text
// layout中声明
{% placeholder footer default %}
    <a href="/contact">联系我们</a>
{% endplaceholder %}

// page中定义
{% put footer %}
    <br>
    <a href="/right">版权声明 put</a>
    <br>
    {% default %}
{% endput %}
```

上面在页面中，我们不仅定义了footer的具体内容， 还将footer的默认内容通过 {% default %}引入了进来。

### 检查placeholder是否存在

```markup
{% if placeholder('footer') %}
    <div class="row">
        <div class="col-md-3">
            {% placeholder footer %}
        </div>
        <div class="col-md-9">
            {% page %}
        </div>
    </div>
{% else %}
    {% page %}
    <p>Welcome.</p>
{% endif %}
```

## {% scripts %}

此标签能输出当前页面所有引用的js文件的script标签代码，一般用在页面的body标签结束前，例如

```markup
<body>
    ...
    {% scripts %}
</body>
```

我们可以通过在页面文件中的“代码”部分定义`onStart()`方法和`put scripts`标签的办法进行增加页面需要的js文件，如下

```markup
function onStart()
{
    $this->addJs('assets/js/app.js');
}

{% put scripts %}
    <script type="text/javascript" src="/themes/demo/assets/js/menu.js"></script>
{% endput %}
```

{% hint style="warning" %}
通过addJs方法会累加所有的js资源，通过put的方法会将所以引用的js重置为put标签里面的js资源，所以两种方法尽量只用一种。
{% endhint %}

## {% styles %}

此标签能输出当前页面所有引用的css样式link标签代码，一般用在布局文件的head标签里面，例如

```text
<head>
    ...
    {% styles %}
</head>
```

和scripts标签一样，我们也可以在页面的“代码”区使用`onStart()`方法和通过 `put styles`来增加页面需要的css文件，如下

```text
function onStart()
{
    $this->addCss('assets/css/hello.css');
}

{% put styles %}
    <link href="/themes/demo/assets/css/page.css" rel="stylesheet" />
{% endput %}
```

同样和scripts标签一样，通过put styles的方法会覆盖原先引入的样式文件。

## {% verbatim %}

此标签是为了输出页面中不想被模板标签语法解析的文本，例如 想输出{{name}} 这几个带大括号的字符，就可以使用verbatim标签。具体例如

```text
{% verbatim %}<p>Hello, {{ name }}</p>{% endverbatim %}
// 这样会直接输出<p>Hello, {{ name }}</p>，而不会被浏览器解析
```

这样就方便了有同样语法的AngularJS来渲染内容。

## {% for %}

此标签能遍历一个数组，基本用法如下

```markup
<ul>
    {% for user in users %}
        <li>{{ user.username }}</li>
    {% endfor %}
</ul>

// 输出数组的key
<ul>
    {% for key, user in users %}
        <li>{{ key }}: {{ user.username }}</li>
    {% endfor %}
</ul>

// 当users为空的时候，我们可以使用else
<ul>
    {% for user in users %}
        <li>{{ user.username }}</li>
    {% else %}
        <li><em>There are no users found</em></li>
    {% endfor %}
</ul>

// 可以在遍历的时候加上 条件判断
<ul>
    {% for key, list in syxwlbt.posts if key < 2 %}
    <li><a href="{{list.url}}" target="_blank">{{list.title}}</a></li>
    {% endfor %}
</ul>
```

{% if %}

此标签用来进行页面的逻辑判断，可以判断变量的Boolean值和数组是否为空等等，例如

```markup
{% if online == false %}
    <p>站点维护中.</p>
{% endif %}

// 判断是否为空
{% if users %}
    <ul>
        {% for user in users %}
            <li>{{ user.username }}</li>
        {% endfor %}
    </ul>
{% endif %}

// if elseif else 
{% if a.isok %}
    a is ok.
{% elseif b.isok %}
    b is ok.
{% else %}
   not ok.
{% endif %}

// if not 
{% if not user.subscribed %}
   <p>订阅列表为空</p>
{% endif %}
```

### 判断变量是否已经定义

```text
{% if users is defined %} 
```

### true&false判断规则

| 变量类型 | 布尔值 |
| :--- | :--- |
| _空字符串_ | false |
| 数字0 | false |
| _空格字符_ | true |
| _空数组_ | false |
| _null_ | false |
| 非空数组 | true |
| 对象 | true |

## {% list %}

用来循环显示内容列表稿件的标签

```markup
<ul>
    {% list 'cid="Q3Dlja12" offset=4 size=5 keyname="i" name="_item" ' %}
        <li><a href="{{_item.url}}">{{_item.title}}</a></li>
    {% endlist %}
</ul>

<ul>
    {% list 'cid="Q3Dlja12" page=2 size=5 keyname="i" name="_item" ' %}
        <li><a href="{{_item.url}}">{{_item.title}}</a></li>
    {% endlist %}
</ul>
```

| 参数 | 描述 |
| :--- | :--- |
| cid | 内容列表的ID |
| page | 分页数 |
| offset | 数据偏移量，类似数据offset，和page参数只填一个 |
| size | 分页大小 |
| keyname | 为`i`即可 |
| name | 循环变量别名 |



