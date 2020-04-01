# 页面\(Pages\)

## 介绍

每个网站都是由很多页面组成的，此功能能新增网站的页面，用来显示单一内容或者嵌套的动态内容。创建的文件都在主题的pages目录下面，文件后缀为htm，支持二级目录（即支持创建文件名为subdirectory/index.htm）

## 属性

| 属性名 | 描述 |
| :--- | :--- |
| 标题 | 网页标题，可使用在网页的&lt;title&gt;&lt;/title&gt;标签中 |
| URL | 页面的访问地址 |
| 布局 | 当前页面选择的布局文件 |
| 描述 | 当前页面的简单备注描述 |
| 标记 | 自定义的html标签、文本内容及其他嵌套的内容 |
| 代码 | 能够对当前页面进行自定义的PHP逻辑代码开发 |

## 注意！！

自定义模板中至少需要有下面三个文件 ，才能支持站点内容页、列表页和首页的预览功能

| 功能 | 文件名 | URL |
| :--- | :--- | :--- |
| 首页 | index.htm | / |
| 列表页 | category.htm | /:category/index.html |
| 内容页 | content.htm | /post/:contentid |

## 用法

### 属性变量的使用

当定义了页面的标题和描述后，我们可以在页面中引用这两个变量，使用语法如下

```markup
...
<title>{{this.page.title}}</title>
...
<meta name="description" content="{{this.page.description}}">
```

### URL匹配语法

每个页面需要指定它的URL，这样在能通过URL获取到指定的数据，系统支持下面多种类型的URL格式定义

{% hint style="warning" %}
定义URL时，请以/开头
{% endhint %}

#### 1. 固定字段的URL格式

```text
/post
```

#### 2. 带可变参数的URL格式

```text
/post/:contentid

## 可以响应的URL请求
/post/abc
/post/xyz.htm等
```

`contentid`变量的值可以在当前页面编辑器的代码区域中通过增加如下代码获取

```text
function onStart()
{
    $contentId = $this->param('contentid');
}
```

#### 3. 带可选的可变参数的URL格式

上面的URL格式需要`contentid`不能为空，有时候参数需要可选，我们可以通过在参数后面加上**?**来实现，如下

```text
/post/:contentid?
```

{% hint style="warning" %}
当url定义如下时，可选参数的功能将会失效

/post/:contentid?/comments

此时url中的:contentid不能为空，否则将会404
{% endhint %}

#### 4. 带可选默认值的可变参数的URL格式

当我们URL中定义的参数为空时，我们可以指定一个默认的值，如下

```text
/post/:contentid?1
```

#### 5. 指定可变参数数据类型的URL格式

我们可以对URL的可变参数的数据类型通过正则表达式来指定，例如下面

```text
/post/:contentid|^[0-9]+$/comments
## 可以响应的URL请求
/post/10/comments

/post/:contentid|^[0-9]+$
## 可以响应的URL请求 
/post/1

/post/:contentid?|^[a-z0-9\-]+$
## 可以响应的URL请求 
/post/fisrt-article
```

#### 6. 通配匹配的URL格式

```text
/post/:category*/:contentid
## 可以响应的URL请求
/post/life/study/2
/post/life/study/program/3
```

上面的`category`变量分别匹配到的值为`life/study`,`life/study/program`

### 注入自定义变量值到页面

在页面的编辑器中我们除了提供‘“标记”来编写html的代码，我们还提供了“代码”的区域，用来更高权限的功能自定义。 通过代码区域编写PHP脚本，我们能实现ajax请求的动态处理、特殊数据的注入等功能。

```php
<?php 
function onStart()
{
    $this['situoyun'] = 'Hello Situoyun!';
}

function onEnd()
{
    $this->page->title = "I have a new Title.";
    $this->page->description = "I have a new Description.";
}
```

通过使用`onStart()`方法的定义，当页面加载开始前，我们能够实现页面变量的插入，和对已有变量的修改，通过使用`onEnd()`方法的定义，当页面加载完成后，我们能对页面title、description进行修改。

```text
{{situoyun}}
{{this.page.title}}
{{this.page.description}}
```

### 返回自定义的Response内容

通过页面编辑器的“代码”功能，我们还能实现页面的特定输出数据功能

```php
function onStart()
{
    return 'Hello world!';  // 页面返回字符串
}

public function onStart()
{
    return Redirect::to('https://www.google.com/'); // 页面重定向
}
```

### 自定义404页面

 当模板的“页面”文件列表中存在URL为`/404`的文件时，系统的404响应会返回此页面的内容，所以我们可以自定义自己独特的404页面。

### 自定义Error页面

当模板的“页面”文件列表中存在URL为`/error`的文件时，系统的500等系统故障响应会返回此页面的内容，我们可以设计自己的错误收集反馈信息页面。

### 注入资源文件

当页面需要加载特定的JavaScript和CSS文件时，我们可以动态的添加到页面中，使用方法如下：

```php
function onStart()
{
    // $this->addCss('assets/css/hello.css');
    $this->addCss(['assets/css/hello.css', 'assets/css/goodbye.css']);
    // $this->addJs('assets/js/app.js');
    $this->addJs(['assets/js/app.js', 'assets/js/nav.js']);
}
```

