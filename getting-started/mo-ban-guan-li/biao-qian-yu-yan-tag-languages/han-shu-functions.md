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

## dump\(\)

打印变量的详细数据，比如变量有哪些属性和方法等

```text
{{ dump(syxwlbt) }}
```

