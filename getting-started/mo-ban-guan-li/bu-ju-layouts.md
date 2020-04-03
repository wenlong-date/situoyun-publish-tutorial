# 布局\(Layouts\)

## 介绍

布局在内容发布系统中的定位是编写可复用的网页基础的页面结构，例如下面

```markup
<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
    <!-- Set render engine for 360 browser -->
    <meta name="renderer" content="webkit">
    <title>{{this.page.title}}</title>
    <meta name="description" content="{{this.page.description}}">
</head>
<body>

{% page %}

</body>
</html>
```

{% hint style="warning" %}
需要在布局的页面中使用 {% page %} 标签，这样当页面应用布局的时候才能正常使用。
{% endhint %}

所有的布局文件都保存在主题的layouts目录下面，文件后缀为htm，支持二级目录（即支持layouts/subdirectory/index.htm目录格式）

## 属性

| 属性名 | 描述 |
| :--- | :--- |
| 描述 | 当前布局的简单备注描述 |
| 标记 | 自定义的html标签、文本内容及其他嵌套的内容 |
| 代码 | 能够对当前布局中进行自定义的逻辑代码开发 |

## 用法

布局可以被页面选择应用，同时布局也能使用部件和内容。

### 布局占位符\(Placeholders\)

有时候不同的页面需要使用同一套布局，但是需要引入的资源文件列表不一样，为了解决这类问题，我们可以使用布局的占位符标签，例如定义下面的布局文件：

```markup
<html>
    <head>
        {% placeholder head %}
    </head>
    ...
```

然后在页面中定义

```markup
{% put head %}
    <link href="/themes/demo/assets/css/page.css" rel="stylesheet">
{% endput %}

<p>Hello Situoyun!</p>
```

我们通过定义`{% placeholder head %}` ，来让页面接管布局的这部分数据的控制权，增强页面的定制化功能。

### 自定义代码逻辑

和页面、部件类似，在布局的“代码”区，我们也提供了可以执行PHP脚本的编辑区，布局可以定义更多的方法，布局的各个方法执行顺序如下：

1. 布局`onInit()` function.
2. 页面`onInit()` function.
3. 布局`onStart()` function.
4. 布局引入的组件`onRun()` method.
5. 布局`onBeforePageStart()` function.
6. 页面`onStart()` function.
7. 页面引入的组件 `onRun()` method.
8. 页面`onEnd()` function.
9. 布局`onEnd()` function.

