# 变量\(Variables\)

下面介绍本系统的一些扩展的变量

## this.page

可以使用下面的示例获取相应的变量

### layout

```text
{{ this.page.layout }}  // 输出 layout名  如  index
```

### id

该变量返回一个包含文件目录和文件名组成的字符串

```markup
<body class="page-{{ this.page.id }}">

// 如果page文件的目录为main/index.htm，那么解析后为
<body class="page-main-index">
```

### title

返回页面填写的标题的数据

```markup
<h1>{{ this.page.title }}</h1>
```

### description

```markup
<p>{{ this.page.description }}</p>
```

### fileName

返回带扩展名的文件名

```markup
<p>{{ this.page.fileName}}</p>
```

### baseFileName

返回不带扩展名的文件名

```markup
<p>{{ this.page.baseFileName}}</p>
```

## this.layout

### id 

该变量返回一个包含文件目录和文件名的组成的字符串，如果布局的文件目录结构为main/index.htm 那么 下面的class值为 layout-main-index

```markup
<body class="layout-{{ this.layout.id }}">
```

### description

```markup
<meta name="description" content="{{ this.layout.description }}">
```

## this.theme

### id

```markup
<body class="theme-{{ this.theme.id }}">
```

### config

```markup
<meta name="description" content="{{ this.theme.config.description }}">
```

## this.param

此变量能够访问到URL中定义的变量数组

例如，URL定义为

```text
/account/:tab
```

```markup
{% if this.param.tab == 'details' %}
    <p>详情页面</p>
{% elseif this.param.tab == 'history' %}
    <p>历史记录页面</p>
{% endif %}
```

也支持下面的写法引用

```markup
{% set name = 'tab' %}

<p>The tab is: {{ this.param[name] }}</p>
```

## this.environment

可以查看当前系统的环境变量

```markup
{% if this.environment == 'test' %}
    <div class="banner">test environment</div>
{% endif %}
```

