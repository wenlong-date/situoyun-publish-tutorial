# 变量\(Variables\)

下面介绍本系统的一些扩展的变量

## this.page

可以使用下面的示例获取相应的变量

### layout

```text
{{ this.page.layout }}  // 输出 layout名  如  index
```

### id

该变量返回一个包含文件目录和文件名的字符串

```markup
<body class="page-{{ this.page.id }}">

// 如果page文件的目录为main/index.htm，那么解析后为
<body class="page-main-index">
```

### title

返回页面填写的标题的数据

```text
<h1>{{ this.page.title }}</h1>
```

### description

```text
<p>{{ this.page.description }}</p>
```

### fileName

返回带扩展名的文件名

```text
<p>{{ this.page.fileName}}</p>
```

### baseFileName

返回不带扩展名的文件名

```text
<p>{{ this.page.baseFileName}}</p>
```

