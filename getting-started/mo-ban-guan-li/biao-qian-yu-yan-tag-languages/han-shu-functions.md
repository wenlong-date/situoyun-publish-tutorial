# 函数\(Functions\)

## str\(\)

### str\_limit\(\)

限制输出的字符个数

```markup
<p>{{ str_limit('abcdefghijklmn', 5) }}</p> 
// 输出 abcde...

<p>{{ str_limit('中文中文中文', 5) }}</p> 
// 输出 中文...

<p>{{ str_limit('abcdefghijklmn', 5, '...read more') }}</p> 
// 输出 abcde...read more
```

{% hint style="warning" %}
这里函数的第二参数为字符个数，以英文字符为标准 。

如果要限制输出5个中文字，那么参数应该为10
{% endhint %}

### str\_camel\(\)

输出驼峰格式的字符

```text
{{str_camel('hello situoyun')}}  // 输出 helloSituoyun
```

### str\_studly\(\)

输出首字符大写的驼峰格式字符

```text
{{str_studly('hello situoyun')}}  // 输出 HelloSituoyun
```

### str\_snake\(\)

输出下划线格式的字符

```text
{{ str_snake('hello situoyun') }}  // 输出 hello_situoyun

{{ str_snake('hello situoyun'， '-') }}  // 输出 hello-situoyun
```

### str\_plural\(\)

输出英文单词的复数形式

```text
{{ str_plural('chicken') }}  // 输出 chickens
{{ str_plural('child') }}  // 输出 children
```

## html\(\)

### html\_clean\(\)

过滤带html标签的文本，避免XSS攻击

```markup
{{ html_clean('<script>window.location = "https://www.google.com"</script>') }}
// 输出 window.location = "https://www.google.com"
```

### html\_thumb\(url, width, heigth\)

增加图片地址的size参数，方便获取裁剪后的图片地址，url 为图片地址，width和height为需要的图片的宽和高，单位为px。

```text
// 输出 裁剪的图片地址 https://maple.node2.autops.xyz/media/20191025/967db6cf03c9d98d50e5167df836309959.jpeg?size=100x100
{{html_thumb('https://maple.node2.autops.xyz/media/20191025/967db6cf03c9d98d50e5167df836309959.jpeg', 100, 100)}}
```

## dump\(\)

打印变量的详细数据，比如变量有哪些属性和方法等

```text
{{ dump(syxwlbt) }}
```

## cateDetail\(group\_id\[,page, size, offset\]\)

用来返回[内容列表详情数据](../chang-jian-wen-ti/ru-he-cha-kan-si-tuo-yun-fa-bu-ku-de-shu-ju-ji-zi-duan.md#wang-zhan-qu-dao-nei-rong-lie-biao-xiang-qing)的函数

| 参数字段 | 是否必需 | 说明 |
| :--- | :--- | :--- |
| group\_id | 是 | 内容列表的ID |
| page | 否 | 分页页数，默认1 |
| size | 否 | 分页大小，默认10，最大20 |
| offset | 否 | 数据偏移量，当有此值时，page参数作用无效。 |

```php
{% set var1 = cateDetail('Q3Dlja12', 1, 5) %}
{% set var2 = cateDetail('Q3Dlja12', 1, 5, 2) %}
```

## cateDetailJson\(group\_id\[,page, size, offset\]\)

用来返回[内容列表详情数据](../chang-jian-wen-ti/ru-he-cha-kan-si-tuo-yun-fa-bu-ku-de-shu-ju-ji-zi-duan.md#wang-zhan-qu-dao-nei-rong-lie-biao-xiang-qing) JSON 的函数

| 参数字段 | 是否必需 | 说明 |
| :--- | :--- | :--- |
| group\_id | 是 | 内容列表的ID |
| page | 否 | 分页页数，默认1 |
| size | 否 | 分页大小，默认10，最大20 |
| offset | 否 | 数据偏移量，当有此值时，page参数作用无效。 |

```php
console.log({{cateDetailJson('nq19WyD7')}});
```

## cateChild\(group\_id\)

获取内容列表下一层的子内容列表信息

数据样例：

```php
array:2 [▼
  0 => array:3 [▼
    "id" => "2Zr5Geke"
    "name" => "创业加视觉"
    "slug" => "chuangyejiashijue"
  ]
  1 => array:3 [▼
    "id" => "VnDMd5r4"
    "name" => "创业子列表"
    "slug" => "mqrxlv_VnDMd5r4"
  ]
]
```

```php
{% set childs = cateChild('Q3Dlja12') %}
{% for child in childs %}
    {% set tmpgroup = cateDetail(child.id)  %}
    <p>{{child.name}}</p>
    <ul>
        {% for post in tmpgroup.posts  %}
            <li><a href="{{post.url}}">{{post.title}}</a></li>
        {% endfor %}
    </ul>
    
    <!-- 传参 -->
    {% partial "category/hengtu-list-all" postLists=tmpgroup %}
    
{% endfor %}
```

## cateUrl\(group\_id\)

用来返回内容列表的URL

```php
{{ cateUrl('Q3Dlja12') }}
```

## postDetail\(post\_id\)

用来返回[稿件详情](../chang-jian-wen-ti/ru-he-cha-kan-si-tuo-yun-fa-bu-ku-de-shu-ju-ji-zi-duan.md#wang-zhan-qu-dao-gao-jian-xiang-qing)的函数

```php
{% set detail = postDetail('LgmO6FNq') %}
```

## postDetailJson\(post\_id\)

用来返回[稿件详情](../chang-jian-wen-ti/ru-he-cha-kan-si-tuo-yun-fa-bu-ku-de-shu-ju-ji-zi-duan.md#wang-zhan-qu-dao-gao-jian-xiang-qing) 数据JSON的函数

```php
console.log({{postDetailJson('aj2pMTox')}});
```

## themeFileUrl\(filename\)

用来返回模板文件的URL，当模板文件的URL为`/news/index.html`时，预览模式下返回`/news/index.html`，静态化模式下返回`/index.html`

```php
{{themeFileUrl('news-index')}}
```



