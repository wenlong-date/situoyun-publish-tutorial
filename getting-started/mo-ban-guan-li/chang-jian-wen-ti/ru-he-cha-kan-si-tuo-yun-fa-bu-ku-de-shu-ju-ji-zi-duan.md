# 如何查看思拓云发布库的数据及字段

目前可以通过两种方式查看所有可以在模板中使用的数据

1. 在思拓云后台发布库的网站和APP发布渠道查看内容列表和稿件详情。
2. 通过发布管理提供的数据预览地址查看内容列表和稿件的数据和字段。

### 网站渠道所有内容列表

**预览地址**：https://domain.publish/test/dv/categories?service=1

此接口一般用来查看内容列表的ID信息。

**返回样例**:

```php
array:5 [▼
  "MPDEb8k9" => array:16 [▶]
  "gW1ONMkb" => array:16 [▶]
  "MVDWJxrj" => array:16 [▼
    "id" => "MVDWJxrj"
    "name" => "视觉"
    "slug" => "shijue"
    "desc" => "我是更新了备注的。第二次更新"
    "last_update_at" => 1583842642
    "created_at" => 1583478909
    "order" => 3
    "count" => 0
    "type" => "nav"
    "content_type" => "mix"
    "content_list" => null
    "draggable" => false
    "link" => ""
    "module" => ""
    "channel_id" => "Q3Dlb12g"
    "style" => null
  ]
  "Q3Dlja12" => array:16 [▼
    "id" => "Q3Dlja12"
    "name" => "创业"
    "slug" => "chuangye"
    "desc" => ""
    "last_update_at" => 1583478449
    "created_at" => 1583478449
    "order" => 4
    "count" => 0
    "type" => "nav"
    "content_type" => "mix"
    "content_list" => null
    "draggable" => false
    "link" => ""
    "module" => ""
    "channel_id" => "Q3Dlb12g"
    "style" => null
  ]
  "2Zr5Geke" => array:16 [▶]
]
```

### 网站渠道内容列表子列表信息

**预览地址：**`https://publish.domain/test/dv/groups/Q3Dlja12`

当模板中使用了模板函数`cateChild('group_id')`时，返回的数据字段如下

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

### 网站渠道内容列表详情

**预览地址**：https://publish.domain/test/dv/categories/Q3Dlja12?service=1

在内容列表的模板URL中，如果使用了`:category`参数，并且在预览的URL中，此参数被正确匹配了，那模板中就能使用`categoryData`的变量，变量的数据字段格式和下面一致。

同时，模板中支持模板函数`cateDetail('group_id')`，用来获取列表的详情信息，返回的字段和下面一致。

**返回样例**:

```php
array:1 [▼
  "Q3Dlja12" => array:14 [▼
    "banners" => array:2 [▶]
    "newsletters" => array:2 [▶]
    "tops" => []
    "posts" => array:8 [▼
      0 => array:59 [▶]
      1 => array:59 [▶]
      2 => array:59 [▶]
      3 => array:59 [▶]
      4 => array:59 [▶]
      5 => array:59 [▼
        "post_id" => "LgmO6FNq"
        "draft_id" => "nDMbelBk"
        "group_id" => "Q3Dlja12"
        "title" => "建设新中国最重要的是什么？人才！| 礼赞70年"
        "sub_title" => ""
        "author" => "唐红"
        "editor" => "唐红"
        "publish_at" => 1569354764
        "publish_at_str" => "9月25日"
        "original_publish_at" => 1569354764
        "last_modify_at" => 1569354752
        "brief" => ""
        "keywords" => "中国,回国,人才,钱学森,新中国"
        "summary" => "1949年5月的一天，美国麻省理工学院教授钱学森收到香港大学心理学教授、中国科学工作者协会香港分会负责人曹日昌的来信，信中写道：“北方工业主管人久仰您的大名，只因通讯不便，不能写信问候，特命我致意。"
        "tags" => ""
        "emoji" => ""
        "payload" => ""
        "emoji_pics" => null
        "mp_user_id" => ""
        "is_follow" => false
        "extra_attrs" => ""
        "ad_video" => null
        "category" => ""
        "source_alias" => "中央纪委国家监委网站"
        "source_type" => "reproduce"
        "source_avatar" => ""
        "source_link" => ""
        "source_desc" => ""
        "read_count" => 0
        "comment_count" => 0
        "like_count" => 0
        "is_liked" => false
        "share_link" => "https://share.node2.autops.xyz/articles/2019-09/25/content_LgmO6FNq.html"
        "pic_num" => 0
        "location" => "cmstop"
        "content_type" => "article"
        "content_format" => "html"
        "style" => array:5 [▼
          "data" => array:1 [▼
            0 => array:2 [▼
              "thumb" => "https://shareapp.cyol.com/cmsfile/thumb/1569383475_8415.jpg"
              "url" => "https://shareapp.cyol.com/cmsfile/thumb/1569383475_8415.jpg"
            ]
          ]
          "model" => "1"
          "desc" => "单图"
          "banner" => false
          "banner_url" => ""
        ]
        "click_action" => ""
        "slip_type" => 0
        "slip_url" => ""
        "show_topic_list" => false
        "content_list" => null
        "topic" => null
        "has_video" => false
        "duration" => 0
        "duration_str" => "00:00"
        "orientation" => 1
        "extra" => null
        "category_info" => ""
        "head_title" => ""
        "live_id" => 0
        "more_news" => ""
        "enable_like" => false
        "url" => "https://publish.node2.autops.xyz/detail/LgmO6FNq.html"
        "style_f" => array:5 [▼
          "data" => array:1 [▼
            0 => array:2 [▼
              "thumb" => "https://shareapp.cyol.com/cmsfile/thumb/1569383475_8415.jpg"
              "url" => "https://shareapp.cyol.com/cmsfile/thumb/1569383475_8415.jpg"
            ]
          ]
          "model" => "1"
          "desc" => "单图"
          "banner" => false
          "banner_url" => ""
        ]
        "first_thumb" => "https://shareapp.cyol.com/cmsfile/thumb/1569383475_8415.jpg"
        "first_thumb_ori" => "https://shareapp.cyol.com/cmsfile/thumb/1569383475_8415.jpg"
        "extras" => []
      ]
      6 => array:59 [▶]
      7 => array:59 [▶]
    ]
    "posts_count" => 8
    "count" => 8
    "actions" => array:1 [▶]
    "style" => array:4 [▶]
    "sections" => null
    "brief" => ""
    "title" => ""
    "group_info" => array:16 [▼
      "id" => "Q3Dlja12"
      "name" => "创业"
      "slug" => "chuangye"
      "desc" => ""
      "last_update_at" => 1583478449
      "created_at" => 1583478449
      "order" => 4
      "count" => 0
      "type" => "nav"
      "content_type" => "mix"
      "content_list" => null
      "draggable" => false
      "link" => ""
      "module" => ""
      "channel_id" => "Q3Dlb12g"
      "style" => null
    ]
    "pagination_html" => ""
    "url" => "https://publish.node2.autops.xyz/xiaomei/Q3Dlja12/index.html"
  ]
]
```

### 网站渠道稿件详情

**预览地址**：`https://publish.domain/test/dv/posts/LgmO6FNq?service=1`

在稿件详情的模板URL中，如果使用了`:contentid`参数，并且预览的URL中正确匹配了此参数，则可以再模板中使用`content`变量，其数据字段和下面的一致。

同时模板中支持使用模板函数postDetail\('post\_id'\)，其返回的数据字段结构也和下面一致。

**返回数据**：

```php
array:75 [▼
  "post_id" => "km3RQclX"
  "draft_id" => "V1QZEdrE"
  "group_id" => "LZkmeZkK"
  "title" => "title"
  "sub_title" => ""
  "author" => "author1"
  "editor" => ""
  "publish_at" => 1589521095
  "publish_at_str" => "3天前"
  "original_publish_at" => 1589521095
  "last_modify_at" => 1589856323
  "brief" => ""
  "keywords" => "第一篇,文章"
  "summary" => "z"
  "tags" => ""
  "emoji" => "0"
  "payload" => null
  "emoji_pics" => []
  "mp_user_id" => ""
  "is_follow" => false
  "extra_attrs" => ""
  "ad_video" => null
  "category" => ""
  "source_alias" => "wl"
  "source_type" => "reproduce"
  "source_avatar" => ""
  "source_link" => ""
  "source_desc" => ""
  "read_count" => 0
  "comment_count" => 0
  "like_count" => 0
  "is_liked" => false
  "share_link" => "https://domain/articles/2020-05/15/content_km3RQclX.html"
  "pic_num" => 0
  "location" => "cmstop"
  "content_type" => "article"
  "content_format" => "html"
  "style" => array:5 [▼
    "data" => array:1 [▼
      0 => array:3 [▼
        "id" => 28971
        "thumb" => "https://domain/img/20200515/img_9601fdf922c14333cf78c50490854122dd65.png"
        "url" => "https://domain/img/20200515/img_9601fdf922c14333cf78c50490854122dd65.png"
      ]
    ]
    "model" => "1"
    "desc" => "单图"
    "banner" => false
    "banner_url" => ""
  ]
  "click_action" => ""
  "slip_type" => 0
  "slip_url" => ""
  "show_topic_list" => false
  "content_list" => null
  "topic" => null
  "has_video" => false
  "duration" => 0
  "duration_str" => "00:00"
  "orientation" => 1
  "extra" => null
  "category_info" => ""
  "head_title" => ""
  "live_id" => 0
  "enable_like" => true
  "duty_editor" => ""
  "commit_editor" => "流程编辑1"
  "enable_comment" => true
  "templete" => ""
  "content" => "<p>改标题了1第一篇文章</p>"
  "content_ad" => null
  "enable_report" => true
  "enable_share" => true
  "enable_dislike" => true
  "enable_ad" => false
  "relations" => array:3 [▼
    0 => array:15 [▶]
    1 => array:15 [▼
      "post_id" => "k3VG2T4j"
      "title" => "【栏目修改标题】【从频道列表修改】第一图集"
      "style" => array:5 [▶]
      "payload" => null
      "author" => "wl"
      "source_alias" => "wl"
      "pic_num" => 4
      "content_type" => "image"
      "content_format" => "json"
      "publish_at" => 1589521265
      "publish_at_str" => "3天前"
      "url" => "https://domain/post/k3VG2T4j.html"
      "first_thumb" => "https://domain/img/20200515/img_9601518ea4b1dede2b6a3d72aee28d163fcb.png"
      "first_thumb_ori" => "https://domain/img/20200515/img_9601518ea4b1dede2b6a3d72aee28d163fcb.png"
      "extras" => []
    ]
    2 => array:15 [▶]
  ]
  "more_news" => []
  "relations_ad" => null
  "emoji_value" => 0
  "is_collection" => false
  "type" => "article"
  "keywords_f" => array:2 [▼
    0 => "第一篇"
    1 => "文章"
  ]
  "group_info" => array:18 [▼
    "id" => "LZkmeZkK"
    "name" => "静态化时机"
    "slug" => "0mptdi_LZkmeZkK"
    "desc" => ""
    "last_update_at" => 1589856325
    "created_at" => 1589514611
    "order" => 0
    "count" => 0
    "type" => "nav"
    "content_type" => "mix"
    "content_list" => null
    "draggable" => false
    "link" => ""
    "module" => ""
    "channel_id" => ""
    "style" => null
    "parent_category_list" => null
    "child_category_list" => null
  ]
  "zq_search" => "<!--enpproperty <articleid>km3RQclX</articleid><date>2020-05-15 13:38:15</date><author>author1</author><title>【专题链接标题】从【运营】标题2链接标题更新1第一篇文章静态化</title><keyword>第一篇,文章 ▶"
  "extras" => []
  "comments" => []
  "comments_count" => 0
]
```

### APP渠道内容列表详情

**预览地址**：`https://publish.domain/test/dv/category/28DgaR1x?service=1`

在APP内容列表展示模板的URL中如果使用了`:scategory`参数，则可以在模板中使用`shareCategoryData`变量，变量的数据格式和下面的一致。  列表ID需要在思拓云发布库的APP渠道中查看及获取。

**返回数据**：

```php
array:11 [▼
  "banners" => array:2 [▶]
  "newsletters" => array:2 [▶]
  "tops" => array:1 [▼
    0 => array:54 [▶]
  ]
  "posts" => array:8 [▼
    0 => array:58 [▶]
    1 => array:58 [▶]
    4 => array:58 [▶]
    5 => array:58 [▶]
    6 => array:58 [▶]
    7 => array:58 [▶]
    8 => array:58 [▶]
    9 => array:58 [▼
      "post_id" => "3nPNxTmN"
      "draft_id" => "9n1K9D5v"
      "group_id" => "28DgaR1x"
      "title" => "动画电影莫把“大朋友”拒之门外"
      "sub_title" => ""
      "author" => "记者 李蕾 通讯员 马丽"
      "editor" => ""
      "publish_at" => 1569353739
      "publish_at_str" => "9月25日"
      "original_publish_at" => 1569353739
      "last_modify_at" => 1569353708
      "brief" => ""
      "keywords" => ""
      "summary" => ""
      "tags" => ""
      "emoji" => ""
      "payload" => ""
      "emoji_pics" => null
      "mp_user_id" => ""
      "is_follow" => false
      "extra_attrs" => ""
      "ad_video" => null
      "category" => ""
      "source_alias" => "光明日报"
      "source_type" => ""
      "source_avatar" => ""
      "source_link" => ""
      "source_desc" => ""
      "read_count" => 0
      "comment_count" => 0
      "like_count" => 0
      "is_liked" => false
      "share_link" => "https://share.node2.autops.xyz/articles/2019-09/25/content_3nPNxTmN.html"
      "pic_num" => 0
      "location" => "cmstop"
      "content_type" => "article"
      "content_format" => "html"
      "style" => array:5 [▶]
      "click_action" => "post_uid"
      "slip_type" => 0
      "slip_url" => ""
      "show_topic_list" => false
      "content_list" => null
      "topic" => null
      "has_video" => false
      "duration" => 0
      "duration_str" => "00:00"
      "orientation" => 1
      "extra" => null
      "category_info" => ""
      "head_title" => ""
      "live_id" => 0
      "more_news" => ""
      "enable_like" => false
      "url" => "https://m1.node2.autops.xyz/share/content/3nPNxTmN.html"
      "first_thumb" => "https://shareapp.cyol.com/cmsfile/thumb/1569382500_5636.jpg"
      "first_thumb_ori" => "https://shareapp.cyol.com/cmsfile/thumb/1569382500_5636.jpg"
      "extras" => []
    ]
  ]
  "posts_count" => 8
  "count" => 12
  "actions" => null
  "style" => array:5 [▼
    "data" => array:1 [▼
      0 => array:3 [▼
        "id" => 129660
        "thumb" => "https://maple.node2.autops.xyz/media/20200402/9602a26d079aa1aec66186d6503ce8d96230.jpeg?size=320x180"
        "url" => "https://maple.node2.autops.xyz/media/20200402/9602a26d079aa1aec66186d6503ce8d96230.jpeg"
      ]
    ]
    "model" => "1+"
    "desc" => "大图"
    "banner" => false
    "banner_url" => ""
  ]
  "sections" => null
  "brief" => "我是添加了备注的视觉。"
  "title" => "视觉"
]
```

### APP渠道专题列表详情 

**预览地址：**https://publish.domain/test/dv/test/dv/special/MVDWVorj

专题的ID在思拓云发布库的发布管理-&gt;专题管理中可以看到每个专题的详情，其中就能看到其ID

**返回数据：**

```php
array:2 [▼
  "home" => array:14 [▼
    "banners" => array:2 [▶]
    "newsletters" => array:2 [▶]
    "tops" => null
    "posts" => null
    "posts_count" => 0
    "count" => 0
    "actions" => null
    "title" => "SARS专题"
    "brief" => "SARS专题2"
    "style" => array:5 [▼
      "data" => array:1 [▼
        0 => array:3 [▼
          "id" => 129795
          "thumb" => "https://maple.node2.autops.xyz/media/20200403/9602740e8095f4e680571db92933fc876949.png?size=320x180"
          "url" => "https://maple.node2.autops.xyz/media/20200403/9602740e8095f4e680571db92933fc876949.png"
        ]
      ]
      "model" => "1+"
      "desc" => "25:9 大图"
      "banner" => false
      "banner_url" => ""
    ]
    "share_link" => "https://share.node2.autops.xyz/special/MVDWVorj.html"
    "groups" => array:3 [▶]
    "sections" => array:3 [▶]
    "id" => "MVDWVorj"
  ]
  "all" => array:3 [▼
    "xRkxMp17" => array:12 [▼
      "banners" => array:2 [▶]
      "newsletters" => array:2 [▶]
      "tops" => null
      "posts" => array:8 [▼
        0 => array:58 [▼
          "post_id" => "Q49QbhOB"
          "draft_id" => "vrGqEQqk"
          "group_id" => "xRkxMp17"
          "title" => "总书记关心的百姓身边事丨留学生遍布世界100多个国家和地区 逾八成选择回国发展——中国教育“引进来”“走出去”取得新成效"
          "sub_title" => ""
          "author" => "吴蕴聪"
          "editor" => ""
          "publish_at" => 1568653199
          "publish_at_str" => "9月17日"
          "original_publish_at" => 1568653199
          "last_modify_at" => 1568652915
          "brief" => ""
          "keywords" => "习近平,中国,王超,马可,没有"
          "summary" => "改革开放四十多年来，中国教育在“引进来”的同时大踏步地“走出去”，通过引进优质教育资源，合作培养高层次人才等举措，包容、借鉴、吸收各种文明的优秀成果，加强人文交流，增进民心相通。"
          "tags" => ""
          "emoji" => ""
          "payload" => ""
          "emoji_pics" => null
          "mp_user_id" => ""
          "is_follow" => false
          "extra_attrs" => ""
          "ad_video" => null
          "category" => ""
          "source_alias" => "新华社"
          "source_type" => ""
          "source_avatar" => ""
          "source_link" => ""
          "source_desc" => ""
          "read_count" => 0
          "comment_count" => 0
          "like_count" => 0
          "is_liked" => false
          "share_link" => "https://share.node2.autops.xyz/articles/2019-09/17/content_Q49QbhOB.html"
          "pic_num" => 0
          "location" => "cmstop"
          "content_type" => "article"
          "content_format" => "html"
          "style" => array:5 [▶]
          "click_action" => "post_uid"
          "slip_type" => 0
          "slip_url" => ""
          "show_topic_list" => false
          "content_list" => null
          "topic" => null
          "has_video" => false
          "duration" => 0
          "duration_str" => "00:00"
          "orientation" => 1
          "extra" => null
          "category_info" => ""
          "head_title" => ""
          "live_id" => 0
          "more_news" => ""
          "enable_like" => false
          "url" => "https://m1.node2.autops.xyz/share/content/Q49QbhOB.html"
          "first_thumb" => "https://shareapp.cyol.com/cmsfile/thumb/1568681694_5840.jpg"
          "first_thumb_ori" => "https://shareapp.cyol.com/cmsfile/thumb/1568681694_5840.jpg"
          "extras" => []
        ]
        1 => array:58 [▶]
        2 => array:58 [▶]
        3 => array:58 [▶]
        4 => array:58 [▶]
        5 => array:58 [▶]
        6 => array:58 [▶]
        7 => array:58 [▶]
      ]
      "posts_count" => 8
      "count" => 8
      "actions" => null
      "style" => array:4 [▶]
      "sections" => null
      "brief" => ""
      "title" => "重点关注"
      "url" => "https://m1.node2.autops.xyz/share/category/xRkxMp17"
    ]
    "j01nglrW" => array:12 [▼
      "banners" => array:2 [▶]
      "newsletters" => array:2 [▶]
      "tops" => null
      "posts" => array:4 [▶]
      "posts_count" => 4
      "count" => 4
      "actions" => null
      "style" => array:4 [▶]
      "sections" => null
      "brief" => ""
      "title" => "其他新闻"
      "url" => "https://m1.node2.autops.xyz/share/category/j01nglrW"
    ]
    "wqkNYND6" => array:12 [▼
      "banners" => array:2 [▶]
      "newsletters" => array:2 [▶]
      "tops" => null
      "posts" => array:5 [▶]
      "posts_count" => 5
      "count" => 5
      "actions" => null
      "style" => array:4 [▶]
      "sections" => null
      "brief" => ""
      "title" => "疫情下的武汉"
      "url" => "https://m1.node2.autops.xyz/share/category/wqkNYND6"
    ]
  ]
]
```

### 中青号主页数据

**预览地址**：`https://publish.domain/test/dv/mp/a7940d80-e5ea-4977-9b40-cb797f68ff6b`

其中最后的中青号个人用户ID需要通过思拓云后台获取。在中青号分享的模板URL中，如果使用了`:mpuid` 参数，并且在预览的URL中正确匹配了参数，模板中可以使用`mpInfo`变量，此变量的数据格式和下面的一致。

**返回数据**：

```php
array:11 [▼
  "id" => "a7940d80-e5ea-4977-9b40-cb797f68ff6b"
  "name" => "想怎么变就怎么变"
  "avatar" => "https://oss.situoyun.com/media/pic/9667fe51ff6cca997dbe3b4c614c022461.gif?size=100x100"
  "introduce" => ""
  "remark" => "哈哈"
  "type" => 1
  "is_follow" => false
  "fans" => 0
  "share_link" => "https://i.cyol.com/appshare/mp/a7940d80-e5ea-4977-9b40-cb797f68ff6b"
  "content_count" => 2
  "contents" => array:2 [▼
    0 => array:23 [▼
      "post_id" => "DLo2OSar"
      "title" => "这是一个小视频"
      "author" => "a7940d80-e5ea-4977-9b40-cb797f68ff6b"
      "content_type" => "article"
      "content_format" => "html"
      "publish_at" => 1585038703
      "publish_at_str" => "3月25日"
      "comment_count" => 0
      "star_count" => 0
      "pic_num" => 0
      "is_follow" => false
      "mp_user_id" => "a7940d80-e5ea-4977-9b40-cb797f68ff6b"
      "source_alias" => "a7940d80-e5ea-4977-9b40-cb797f68ff6b"
      "source_avatar" => "https://oss.situoyun.com/media/pic/9667fe51ff6cca997dbe3b4c614c022461.gif?size=100x100"
      "style" => array:5 [▼
        "data" => array:1 [▼
          0 => array:2 [▼
            "thumb" => "https://oss.situoyun.com/media/20200221/967cbeaffa8716a908738d4ed2cdbb5314.jpeg"
            "url" => "https://oss.situoyun.com/media/20200221/967cbeaffa8716a908738d4ed2cdbb5314.jpeg"
          ]
        ]
        "model" => "1"
        "desc" => "单图"
        "banner" => false
        "banner_url" => ""
      ]
      "topic" => null
      "duration" => 0
      "duration_str" => "00:00"
      "orientation" => 1
      "status" => 0
      "is_liked" => false
      "like_count" => 0
      "share_link" => "https://share.situoyun.com/articles/2020-03/24/content_DLo2OSar.html"
    ]
    1 => array:23 [▶]
  ]
]
```

### 稿件评论的数据

**预览地址**：`https://publish.domain/test/dv/comments/rdG20in1`

此接口的数据在「网站渠道稿件详情」中的comments字段已经返回。

**返回数据**：

```php
array:2 [▼
  "comments" => array:3 [▼
    0 => array:20 [▼
      "id" => 9
      "gid" => "756950a4-332b-478f-9b27-f21d6353f045"
      "owner_user_id" => "anonymous"
      "target_user_id" => ""
      "avatar" => ""
      "alias" => "匿名用户"
      "parent_id" => ""
      "comment_type" => 0
      "media_id" => "rdG20in1"
      "reply_count" => 0
      "content" => "加油3"
      "state" => 2
      "star_count" => 0
      "star" => false
      "reply_alias" => ""
      "is_hot" => false
      "user" => null
      "created_at" => 1585797925
      "created_at_str" => "刚刚"
      "updated_at" => 1585797925
    ]
    1 => array:20 [▶]
    2 => array:20 [▶]
  ]
  "count" => 3
]
```

