# 内容列表和稿件等url字段处理逻辑说明

## 内容列表url字段

作用范围：通过`categoryData.url`、`cateUrl('group_id')`、`cateDetail('group_id')`方法获取到的内容列表的url字段。

```php
function 获取内容列表url(Q3Dlja12)
    如果是静态化场景
    return /Q3Dlja12/index[_1|2|3].html

    默认列表模板文件名category.htm 其模板文件设置的URL为 /:category/index.html

    如果Q3Dlja12绑定了列表首页模板文件
        绑定模板文件名 a/category.htm 其模板文件设置URL为 /a/:cateogry/index.html
        return https://domain/a/Q3Dlja12/index.html

    return https://domain/Q3Dlja12/index.html
```

## 稿件详情url字段

作用范围：通过`categoryData.posts`、`cateDetail('group_id')`获取的posts和`postDetail('post_id')`等获取到的稿件的url字段。

```php
function 获取稿件url(LgmO6FNq)
    如果是静态化场景
    return /articles/2019-09/25/content_LgmO6FNq.html

    默认稿件详情模板文件名content.htm 其模板文件设置URL为 /post/:contentid

    如果稿件ID LgmO6FNq 的group_id是Q3Dlja12，并且Q3Dlja12绑定了稿件详情模板文件
        绑定的详情模板文件名 b/content.htm 其模板文件设置URL为 /b/post/:contentid
        return https://domain/b/post/LgmO6FNq.html

    return https://domain/post/LgmO6FNq.html
```

## APP渠道内容列表url字段

作用范围：专题数据通过`specials`字段获取子内容列表的url时。

```php
function APP内容列表url(28DgaR1x)
    如果是静态化场景
    return /28DgaR1x/index.html

    如果存在文件名为share/category.htm的模板文件，其模板设置的URL为/share/category/:scategory
        return https://domain/share/category/28DgaR1x.html

    return '#'
```

## APP渠道稿件详情的url字段

作用范围：通过`shareCategoryData.posts`、`specials`下稿件的posts 时获取到的稿件url

```php
function APP稿件详情url(gGB3KCQL)
    如果是静态化场景
    return /articles/2019-09/25/content_gGBj0tQL.html

    content_type和模板文件名对应表maps：
        article  => share/content.htm (url设置为share/post/:contentid)
        image    => share/image.htm (url设置为share/image/:contentid)
        video    => share/video.htm (url设置为share/video/:contentid)
        svideo   => share/svideo.htm (url设置为share/svideo/:contentid)
        audio    => share/audio.htm (url设置为share/audio/:contentid)
        link     => share/link.htm (url设置为share/link/:contentid)
        h5       => share/link.htm (url设置为share/link/:contentid)
        activity => share/activity.htm (url设置为share/activity/:contentid)


    如果稿件content_type对应的模板文件存在
        return https://domain/share/{content_type}/gGBj0tQL.html

    return '#'
```



