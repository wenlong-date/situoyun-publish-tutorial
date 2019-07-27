# 过滤器\(Filters\)

## \|app

此过滤器能返回网站域名拼接参数后的URL，例如下面

```markup
<link rel="icon" href="{{ '/favicon.ico'|app }}" />

<a href="{{ '/about-us'|app }}">
    About Us
</a>
```

如果网站的域名为`https://publish.situoyun.com（下面的过滤器都以此域名为网站域名）`，经过过滤器后输出的内容为

```markup
<link rel="icon" href="https://publish.situoyun.com/favicon.ico" />

<a href="https://publish.situoyun.com/about-us">
    About Us
</a>
```

## \|page

此过滤器的参数是不带后缀的文件名，返回页面对应的URL地址，例如下面

```markup
<a href="{{ 'about'|page }}">About Us</a>

// about.htm 页面文件 设置的url 为 /more/about-us, 那上面的会输出
<a href="https://publish.situoyun.com/more/about-us">About Us</a>
```

创建当前页面的URL的方法是将参数写为空字符串，例如下面

```markup
<a href="{{ ''|page }}">Current page</a>
```

### 输出带URL参数的页面URL

如果有个url为`/post/:contentid`的名为content.htm的页面文件，如果要使用这个页面来创建连接，可以用下面的方法

```markup
<a href="{{ 'content'|page({ contentid: 10 }) }}">
    contentid is 10
</a>

// 上面结果解析后的数据为
<a href="https://publish.situoyun.com/post/10">
    contentid is 10
</a>

// 配合上数据遍历
<ul>
    {% for key, list in syxwlbt.posts %}
    <li><a href="{{'content'|page({'contentid': list.post_id})}}{{list.url}}" target="_blank">{{list.title}}</a></li>
    {% endfor %}
</ul>
```

## \|theme

此过滤器常用在我们需要引入应用当前主题资源文件的时候，例如

```markup
<script type="text/javascript" src="{{ 'assets/js/index.js'|theme }}"></script>

// 上面解析后输出数据为
<script type="text/javascript" src="https://publish.situoyun.com/themes/themename/assets/js/index.js"></script>

// 批量的引入文件
<link href="{{ [
    'assets/css/styles1.css',
    'assets/css/styles2.css'
]|theme }}" rel="stylesheet">
```

## \|md

此过滤器能解析markdown格式的文本然后输出对应的html文本，例如

```markup
{{ '**Text** is bold.'|md }}

// 解析输出为
<strong>Text</strong> is bold.
```

## \|raw

此过滤器的作用是允许浏览器解析要输出的字符中的标签，我们常用在显示文章的详情内容时，需要浏览器对带html标签的内容详情进行解析，使用方法为

```text
{% set htm="<a href='http://www.cmstop.com' target='_blank'>cmstop</a>" %}

{{htm}}
// 这样会直接输出  <a href='http://www.cmstop.com' target='_blank'>cmstop</a> 字符串显示在页面中

{{htm|raw}}
// 这样会将a标签解析成网页的DOM元素
```

## \|default

此过滤器的作用是当要输出的变量未定义或者为空时，输出定义的默认值，用法如下

```text
{{ variable|default('未定义的变量') }}

{{ variable.foo|default('属性foo未定义') }}

{{ variable['foo']|default('数组variable中元素foo未定义') }}

{{ ''|default('变量为空')  }}
```

