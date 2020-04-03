---
description: 下面中的各类数据的字段可以参考「如何查看思拓云发布库的数据及字段」
---

# 模板中引入各类数据使用参考

## 使用内容列表数据显示

### 使用`categoryData`变量

使用此变量的前提是模板的URL参数中有`:category`，并且预览的地址中此参数被正确匹配了。例如模板文件URL为`/:category/index.html`，预览地址为`/Q3Dlja12/index.html`。

```markup
<h1>{{categoryData.group_info.name}}</h1>
<ul>
    {% for post in categoryData.posts %}
    <li><a href="{{post.url}}">{{post.title}}</a></li>
    {% endfor %}
</ul>
```

{% hint style="warning" %}
可以在模板页面中设置分页大小，来控制返回的稿件条数，目前最多只能返回**20**条。
{% endhint %}

### 使用`cateDetail`方法获取数据

这里使用了set标签用来暂存数据。

> cateDetail\('group\_id'\[, page = 1, size = 10, offset\]\) 
>
> 函数接收四个参数，第一个必需，后三个非必需，第一个为PC渠道内容列表ID，第二个为第几页，第三个为分页大小（最大支持20），最后一个是偏移量，如果offset存在则page将会失效。

```markup
{% set var1 = cateDetail('Q3Dlja12', 1, 5) %}
<h1>{{var1.group_info.name}}</h1>
<ul>
    {% for post in var1.posts %}
        <li><a href="{{post.url}}">{{post.title}}</a></li>
    {% endfor %}
</ul>
```

### 使用list标签

> list标签使用时需要六个参数 ：
>
> `cid`为PC渠道内容列表的ID，`offset`表示读取数据时的偏移量（类似数据库的`offset`）,当有`offset`的时候`page`参数不生效，`page`表示第几页开始，`size`表示每页稿件数量，`keyname`默认为`i`即可，`name`的为每个稿件数据保存的变量名。

```markup
<ul>
    {% list 'cid="Q3Dlja12" offset=1 size=5 keyname="i" name="_item" ' %}
        <li><a href="{{_item.url}}">{{_item.title}}</a></li>
    {% endlist %}
</ul>
```

{% hint style="info" %}
其中list和cateDetail区别是，cateDetail能获取更详情的信息，list相当于只循环显示了cateDetail中的posts字段的数据。
{% endhint %}

## 显示稿件详情的数据

### 使用content变量

使用此变量的前提是模板的URL中有:contentid的参数，访问的域名中正确匹配上了此参数。例如，模板的URL为/post/:contentid，然后预览稿件的URL为/post/LgmO6FNq。

```markup
<h1>{{content.title}}</h1>
<p>发布时间：{{content.publish_at|date('Y-m-d H:i:s')}}</p>

{{content.content|raw}}

<p>编辑：{{content.editor}}</p>
```

### 使用postDetail\('post\_id'\)函数

```markup
{% set detail = postDetail('LgmO6FNq') %}

<h1>{{detail.title}}</h1>
<p>发布时间：{{detail.publish_at|date('Y-m-d H:i:s')}}</p>

{{detail.content|raw}}

<p>编辑：{{detail.editor}}</p>
```

## 显示APP渠道内容列表数据

### 使用`shareCategoryData`变量

使用此变量的前提是模板的URL中有`:scategory`的参数，访问的域名中正确匹配上了此参数。例如，模板的URL为`/share/category/:scategory`。

```markup
<h1>{{shareCategoryData.title}}</h1>
<p>{{shareCategoryData.brief}}</p>

<ul>
    {% for post in shareCategoryData.posts %}
        <li><a href="{{post.url}}">{{post.title}}</a></li>
    {% endfor %}
</ul>
```

## 显示APP渠道专题的数据

### 使用`specials`变量

使用此变量的前提是模板的URL中有`:special`的参数，访问的域名中正确匹配了此参数。例如，模板的URL为`/share/special/:special` [专题的数据预览地址](ru-he-cha-kan-si-tuo-yun-fa-bu-ku-de-shu-ju-ji-zi-duan.md#app-qu-dao-zhuan-ti-lie-biao-xiang-qing)

```markup
<h1>{{specials.home.title}}</h1>
{% for group in specials.all %}
    <h2>{{group.title}}</h2>
    <ul>
        {% for post in group.posts %}
            <li><a href="{{post.url}}">{{post.title}}</a></li>
        {% endfor  %}
    </ul>
    
{% endfor %}
```

## 显示中青号的主页数据

### 使用`mpInfo`变量

```markup
<h1>{{mpInfo.name}}</h1>

<ul>
    {% for post in mpInfo.contents %}
        <li>{{post.title}}</li>
    {% endfor %}
</ul>

```



