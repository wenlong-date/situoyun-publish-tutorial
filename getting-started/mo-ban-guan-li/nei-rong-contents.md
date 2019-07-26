# 内容\(Contents\)

## 介绍

内容在内容发布系统中的定位是编写可以复用的htm，markdown和txt的文件，然后可以应用在页面、部件、布局中。

## 用法

### 基本用法

定义一个contact.md的content文件

```text
## This is a contact

Our webSite is [cmstop]({url})
```

使用方法为

```text
{% content "contact.md" url="http://www.cmstop.com" %}
```

我们看到，内容的引用也可以传递参数。

{% hint style="warning" %}
需要注意的是，内容和页面、部件、布局有些差别

1. 引用的文件需要加上后缀名
2. 内容使用参数时只需要一个大括号，即 `{param}` 即可
{% endhint %}

