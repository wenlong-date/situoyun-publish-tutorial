# 主题\(Themes\)

## 基本信息

主题是对网站整体风格的定义，内容发布系统中提供了对主题风格模板编辑修改的功能，用户能高度自定义页面显示的内容和样式，并且能够定义多套模板进行整站切换。

每套网站主题都由页面、部件、布局、内容和资源文件夹下的文件组建起来，下面介绍下各类文件夹的文件区别。

| 主题基本对象 | 功能描述 |
| :--- | :--- |
| 页面 | 每个页面的展示内容的代码。例如网站首页内容的显示布局结构代码，引入其他部件的代码等。 |
| 部件 | 网站通用性的代码。例如网站通用的导航栏代码，脚部版权，联系方式等介绍代码等。 |
| 布局 | 网站各类页面通用的html代码。例如定义通用的&lt;html&gt;&lt;head&gt;&lt;meta&gt;&lt;link&gt; &lt;script&gt;&lt;body&gt;&lt;/body&gt;&lt;/html&gt;等代码 |
| 内容 | 网站通用的内容。支持Text,HTML和Markdown格式的文件编辑和解析。 |
| 资源 | 保存和编辑网站所需的Images,CSS和JavaScript的文件。 |

## 文件结构

每套主题都是一定特定名称的文件夹，文件夹下面有`pages`、`partials`、`content`、`layouts`、`assets`文件夹及`theme.yaml`文件，目录结构如下

```text
themename/       <=== 主题名称
pages/           <=== Pages文件夹
  home.htm    
  blog/          <=== Pages的子文件夹
    category.htm
    archive.htm
layouts/         <=== Layouts文件夹
  default.htm
partials/        <=== Partials文件夹
  sidebar.htm
  blog/          <=== Partials子文件夹
    category-list.htm
content/         <=== Content文件夹
  intro.htm
assets/          <=== Assets文件夹
  css/
    my-styles.css
  js/
  images/
```

### 文件层级

`pages`、`partials`、`content`和`layouts`当前支持二级目录，即支持文件结构为pages/home.htm 和 pages/blog/category.htm，不支持pages/blog/first-blog/index.htm结构。

`assets`的文件支持多级目录，文件存储更为灵活。

### 文件和文件夹命名规范

文件和文件夹命名中只能出现 **数字** 、**字母** 、**下划线\(\_\)**、**英文破折号\(-\)**

### 文件和文件夹创建方式

要实现创建layouts/main/index.htm结构的文件，可以在布局的页面中创建文件，在文件名的输入框中 数据 **main/index** 或者 **main/index.htm** 没有加上.htm 系统会自动给文件加上.htm的后缀。

要实现创建assets/js/jquery/jquery.min.js结构的文件，可以在资源的页面中创建文件，在文件名的输入框中填写 **js/jquery/jquery.min.js**

{% hint style="warning" %}
资源类型的文件新建文件支持的后缀名为css, js, less, sass, scss

上传的文件格式支持jpg, jpeg, bmp, png, webp, gif, ico, css, js, woff, woff2, svg, ttf, eot, json, md, less, sass, scss, xml
{% endhint %}

