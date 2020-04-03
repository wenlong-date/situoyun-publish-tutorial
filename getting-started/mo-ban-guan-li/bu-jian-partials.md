# 部件\(Partials\)

## 介绍

部件在内容发布系统中的作用是定义可复用的代码块和功能区域，例如首页，列表页，专题页面都需要的导航、底部的企业介绍和版权信息等。通过一行代码就能在网站的各个页面、布局中复用功能，修改一处，全局都可以更新。创建的文件都在主题的partials目录下面，文件后缀为htm，支持二级目录（即支持partials/subdirectory/index.htm目录格式）

属性

| 属性名 | 描述 |
| :--- | :--- |
| 绑定内容数据 | 当前部件绑定的思拓云内容列表 |
| 描述 | 当前部件的简单备注描述 |
| 标记 | 自定义的html标签、文本内容及其他嵌套的内容 |
| 代码 | 能够对当前部件进行自定义的逻辑代码开发 |

## 用法

### 基本用法

创建一个footer的partial文件

```markup
<div class="footer">
    <ul>
        <li><a href="#">版权声明</a></li>
        <li>|</li>
        <li><a href="#">公司介绍</a></li>
        <li>|</li>
        <li><a href="{{url}}">联系我们</a></li>
        ...
    </ul>
    <p>xx公司版权所有，未经许可xx</p>
</div>
```

即可通过下面的方式在页面和布局中使用

```text
{% partial "footer" url="http://www.cmstop.com" %}
```

其中不仅能复用html代码块，还能传递参数，实现部件的更高的复用度。

### 自定义代码逻辑

在部件的编辑器中，我们也提供了“代码”的功能，里面支持部件的`onStart()`和`onEnd()`方法的定义，分别在部件加载前和加载完成后执行，我们也可以通过这两个方法实现变量的注入。

```php
function onStart()
{
    $this['situoyun'] = "Hello Situoyun!";
}
# 使用
<h3>{{ situoyun}}</h3>
```

{% hint style="warning" %}
部件相比页面在执行onStart\(\)和onEnd\(\)方法中，直接返回特定的数据将不会生效。
{% endhint %}

