---
title: "本hugo博客配置使用说明"
date: 2020-08-18T23:49:11+08:00
draft: false
tags: ["hugo","博客"]
---

# Zzo theme for Hugo - cn

2020-07-24 新功能 - [主标题中的类型写入程序]


我添加了新的主标题选项。现在，我们有5个选项-空，文本，图像，滑块和打字机按照以下步骤进行应用

0. 先更新主题.
1. 在中将“homeHeaderType”参数编辑为“typewriter”参数toml文件。
2. 在你的md头文件中插入下面的代码。
```yaml
header:
  - type: typewriter
    methods:
      - typeString: Hello world!
      - pauseFor: 2500
      - deleteAll: true
      - typeString: Strings can be removed
      - pauseFor: 2500
      - deleteChars: 7
      - typeString: <strong>altered!</strong>
      - pauseFor: 2500
    options:
      loop: true
      autoStart: false
    height: 190
    paddingX: 50
    align: center
    fontSize: 44
    fontColor: yellow
  ...
```
3. 参考本网站https://safi.me.uk/typewriterjs/然后编辑参数。

## 文献资料

[https://zzodocs.netlify.com/docs/](https://zzodocs.netlify.com/docs/)

## 目录

* [特征](#features)
* [最低雨果版本](#minimum-hugo-version)
* [安装](#installation)
* [更新中](#updating)
* [运行示例站点](#run-example-site)
* [组态](#configuration)
* [画廊](#gallery)
* [联系页面](#contact-page)
* [对话页面](#talks-page)
* [展示页面](#showcase-page)
* [多语言](#multi-language)
* [作者](#author)
* [网站图标](#favicon)
* [客制化](#customizing)
* [外部图书馆](#external-library)
* [简码](#shortcodes)

## 特征

* 多种皮肤（深色，浅色，日光化...）
* 移动菜单
* CSS网格和Flex布局
* HTML5
* 雨果管道为JS和SASS
* 简单博客
* 搜索引擎优化（SEO）
* 多语种（i18n）
* 响应式设计
* 的RSS
* 搜索
* 画廊
* 快速突出显示代码
* 对话页面
* 展示页面

## 最低雨果版本

需要Hugo 0.60.0或更高版本。

## 安装

首先，您需要添加配置文件。遵循配置步骤。

然后，您可以从Github手动下载和解压缩主题，但是使用git克隆存储库会更容易。

从您网站的根目录

```bash
$ git clone https://github.com/zzossig/hugo-theme-zzo.git themes/zzo
```

如果强烈建议您使用git对网站进行版本控制，则最好将zzo主题添加为子模块。

从您网站的根目录：

```bash
git submodule add https://github.com/zzossig/hugo-theme-zzo.git themes/zzo
```

## 更新中

从您网站的根目录：

```bash
git submodule update --remote --merge
```

## 运行示例站点

从themes / zzo / exampleSite的根目录：

```bash
hugo server --themesDir ../..
```

## 组态

0. 从站点的根目录：删除config.toml文件并在下面添加文件

1. config文件夹结构。请记住_default文件夹上的下划线

```bash
root
├── config
│   ├── _default
│   │   ├── config.toml
│   │   ├── languages.toml
│   │   ├── menus.en.toml
│   │   ├── params.toml
```

2. config.toml

```bash
baseURL = "http://localhost:1313//" #你的网站的网址。
title = "Hugo Zzo Theme" # 您网站的标题
theme = "zzo" #  theme文件夹的名称。

defaultContentLanguage = "en" # 要使用的默认语言（如果您设置了多语言） 
defaultContentLanguageInSubdir = true # baseURL/en/, baseURL/kr/ ...
hasCJKLanguage = true # 为中文/日文/韩文设置`true`。

summaryLength = 70 # 列表页面上帖子描述的长度。
buildFuture = true # 如果为true，我们可以使用将来的日期作为对话页面

copyright = "©{year}, All Rights Reserved" # 版权符号：$ copy; 当前年份：{year}
timeout = 10000
enableEmoji = true
paginate = 13 # 分页列表中每页的项目数。
rssLimit = 100

enableGitInfo = false # 为 true时，修改日期将显示在摘要和单个页面上。由于需要获取GitHub信息，因此根据您拥有 的页码，此功能的构建速度会变慢
googleAnalytics = ""

[markup]
  [markup.goldmark]
    [markup.goldmark.renderer]
      hardWraps = true
      unsafe = true
      xHTML = true
  [markup.highlight]
    codeFences = true
    lineNos = true
    lineNumbersInTable = true
    noClasses = false
  [markup.tableOfContents]
    endLevel = 3
    ordered = false
    startLevel = 2

[outputs]
  home = ["HTML", "RSS", "JSON"]

[taxonomies]
  category = "categories"
  tag = "tags"
  series = "series"
```

3. languages.toml

```bash
[en]
  title = "Hugo Zzo Theme"
  languageName = "English"
  weight = 1

[ko]
  title = "Hugo Zzo Theme"
  languageName = "한국어"
  weight = 2

[zh]
  title = "Hugo Zzo Theme"
  languageName = "博客名"
  weight = 3
```

4. menus.en.toml

You shoud make your own menu.

```bash
[[main]]
  identifier = "about"
  name = "about"
  url = "about"
  weight = 1

[[main]]
  identifier = "archive"
  name = "archive"
  url = "archive"
  weight = 2

[[main]]
  identifier = "gallery"
  name = "gallery"
  url = "gallery"
  weight = 3
    
[[main]]
  parent = "gallery"
  name = "cartoon"
  url = "gallery/cartoon"

[[main]]
  parent = "gallery"
  name = "photo"
  url = "gallery/photo"

[[main]]
  identifier = "posts"
  name = "posts"
  url = "posts"
  weight = 4
    
[[main]]
  identifier = "notes"
  name = "notes"
  url = "notes"
  weight = 5
...
```

5. params.toml

```bash
logoText = "Zzo" # 显示在网站导航栏中的徽标文本。
logoType = "short" #  long， short- > short：squre形状包含徽标文本，long：矩形形状不包含徽标文本 
logo = true # 出现在站点导航栏中的徽标。
description = "The Zzo theme for Hugo example site." # 为SEO
custom_css = [] # custom_css = ["scss/custom.scss"] and then make file at root/assets/scss/custom.scss
custom_js = [] # custom_js = ["js/custom.js"] and then make file at root/assets/js/custom.js
useFaviconGenerator = false # https://www.favicon-generator.org/
languagedir = "ltr" # ltr / rtl

themeOptions = ["dark", "light", "hacker", "solarized", "kimbie"] # 选择网站颜色主题的选项 
notAllowedTypesInHome = ["contact", "talks", "about", "showcase"] # 主页中不允许使用的页面类型。可以在最前面设置类型，也可以默认为文件夹名称。“关于”， “档案”， “展示柜” ]
notAllowedTypesInHomeSidebar = ["about", "archive", "showcase"] # 不允许在首页侧边栏中显示页面类型（最近的帖子标题）。 
notAllowedTypesInArchive = ["about", "talks", "showcase"] # 不允许存档页面中的页面类型  
notAllowedTypesInHomeFeed = ["about", "archive", "contact", "talks", "showcase", "publication", "presentation", "resume", "gallery"]
enablePinnedPosts = true # 在主视图中首先显示固定的帖子

viewportSize = "normal" # widest, wider, wide, normal, narrow # 最宽，最宽，宽，正常，窄
enableUiAnimation = true
hideSingleContentsWhenJSDisabled = false
minItemsToShowInTagCloud = 1 # 标签云中显示的最小项目

# 头
homeHeaderType = "text" # text, img, slide, typewriter # 文本，IMG，幻灯片，打字机

# 菜单 
showMobileMenuTerms = ["tags", "categories", "series"]

# 导航栏 
enableThemeChange = true # 网站的颜色主题

# body
enableBreadcrumb = true # 列表的面包屑导航，单页
enableSearch = true # 使用Fuse进行站点搜索
enableSearchHighlight = true # 真时，搜索关键字将突出 
enableGoToTop = true # 滚动到顶部 
enableWhoami = true # 在单页结束 
summaryShape = "classic" # card, classic, compact # 卡，经典，紧凑 
archiveGroupByDate = "2006" # "2006-01": group by month, "2006": group by year #  “ 2006-01 ”：按月份分组，“ 2006”：按年份分组
archivePaginate = 13 # 每页项目 
paginateWindow = 1 # 将其设置为1给出7个按钮，2给出9，依此类推。如果设置为1：[1 ... 4 5 6 ... 356] [1 2 3 4 5 .. 356]等
talksPaginate = 8 # 项目每页 
talksGroupByDate = "2006" #  “2006-01”：GROUP BY月， “2006”：GROUP BY年

#  WHOAMI：使用-主页栏，后期单页底部。所有值都可以为空。
myname = "zzossig"
email = "zzossig@gmail.com"
whoami = "Web Developer"
bioImageUrl = "" # 图片网址，例如“ http // ...”或“ images / anyfoldername / mybioimage.jpg” “如果未设置，我们将在root / static / images / whoami / avatar中找到一个头像图片。（png | jpg | svg） 
useGravatar = false # 我们使用此选项的最高优先级 
location = "Seoul, Korea"
organization = "Hugo"
link = "https://github.com/zzossig/hugo-theme-zzo"

# 侧边栏 
enableBio = true # 在主页侧边栏中
enableBioImage = true # 在主页侧边栏中
enableSidebar = true # 设置为false以创建内容的全宽。
enableSidebarTags = true # 如果您想使用标签。
enableSidebarSeries = true
enableSidebarCategories = true
enableHomeSidebarTitles = true
enableListSidebarTitles = true
enableToc = true # 单页目录，您可以将此参数替换为toc（toc = true） 
hideToc = false # 隐藏或显示toc 
tocPosition = "inner" # inner, outer
tocFolding = false
enableTocSwitch = true # 单页目录可见性切换项目 
itemsPerCategory = 5 # 侧栏中显示的最大帖子数。
sidebarPosition = "right" # 生物，轮廓组件的布局位置 
tocLevels = ["h2", "h3", "h4"] # 文章中的最小h2，最大h4 
enableSidebarPostsByOrder = false # 侧边栏中的另一个列表

# 页脚 
showPoweredBy = true # 显示页脚文本：技术雨果和ZZO主题 
showFeedLinks = true #  RSS订阅 
showSocialLinks = true # 电子邮件，Facebook，微博... 
enableLangChange = true # 显示按钮页脚的左下角。

# 服务 
googleTagManager = "" # GTM-XXXXXX
baiduAnalytics = "" # 谷歌分析的替代
enableBusuanzi = false # 如果设置为true，总页面浏览，不重复访客总数页脚显示出来。
busuanziSiteUV = true # 唯一身份访问者（访问者总数） 
busuanziSitePV = true # 网站总页面 
busuanziPagePV = true # 发布次数

# comment
enableComment = true
disqus_shortname = "" 
commento = false

[gitment]          # Gitment是基于GitHub的问题的评论系统。 see https://github.com/imsun/gitment
  owner = ""              # Your GitHub ID
  repo = ""               # The repo to store comments
  clientId = ""           # Your client ID
  clientSecret = ""       # Your client secret

[utterances]       # https://utteranc.es/
  owner = ""              # Your GitHub ID
  repo = ""               # The repo to store comments
  message = ""      # Optional
  link = ""         # Optional

[gitalk]           # Gitalk是基于GitHub的问题的评论系统。 see https://github.com/gitalk/gitalk
  owner = ""              # Your GitHub ID
  repo = ""               # The repo to store comments
  clientId = ""           # Your client ID
  clientSecret = ""       # Your client secret

# Valine.
# You can get your appid and appkey from https://leancloud.cn
# more info please open https://valine.js.org
[valine]
  enable = false
  appId = '你的appId'
  appKey = '你的appKey'
  notify = false  # mail notifier , https://github.com/xCss/Valine/wiki
  verify = false # Verification code
  avatar = 'mm' 
  placeholder = '说点什么吧...'
  visitor = false

[changyan]
  changyanAppid = ""        # Changyan app id             # 畅言
  changyanAppkey = ""       # Changyan app key

[livere]
  livereUID = ""            # LiveRe UID                  # 来必力

# Isso: https://posativ.org/isso/
[isso]
  enable = false
  scriptSrc = "" # "https://isso.example.com/js/embed.min.js"
  dataAttrs = "" # "data-isso='https://isso.example.com' data-isso-require-author='true'"

[socialOptions] # if set, social icons will show up.
  email = "mailto:your@email.com"
  phone = ""
  facebook = "http://localhost:1313//"
  twitter = "http://localhost:1313//"
  github = "https://github.com/zzossig/hugo-theme-zzo"
  stack-overflow = ""
  instagram = ""
  google-plus = ""
  youtube = ""
  medium = ""
  tumblr = ""
  linkedin = ""
  pinterest = ""
  stack-exchange = ""
  telegram = ""
  steam = ""
  weibo = ""
  douban = ""
  csdn = ""
  gitlab = ""
  mastodon = ""
  jianshu = ""
  zhihu = ""
  signal = ""
  whatsapp = ""
  matrix = ""
  xmpp = ""
  dev-to = ""
  gitea = ""
  google-scholar = ""
  twitch = ""

[donationOptions]
  enable = false # 如果设置，则捐赠按钮将显示在单个页面上。
  alipay = "" # 支付宝QR码图片（示例路径：images / donation / alipay-qrcode.png），然后将文件放在root / static / images / donation / 
  wechat = "" # 微信支付QR码图片（示例路径：与上面相同） 
  paypal = "" # Paypal URL
  patreon = "" # Patreon URL
  bitcoin = "" # 示例路径： images/donation/bitcoin-code-image.png

[copyrightOptions]
  enableCopyrightLink = false # 如果已设置，则可以添加版权链接 
  copyrightLink = ""
  copyrightLinkImage = ""
  copyrightLinkText = ""

# possible share name: "facebook","twitter", "reddit", "linkedin", "tumblr", "weibo", "douban", "line", "whatsapp", "telegram"
[[share]]
  name = "facebook"
[[share]]
  name = "twitter"
  username = ""

[[footerLinks]]
  name = ""
  link = ""
[[footerLinks]]
  name = ""
  link = ""
```

## 画廊

有两种制作画廊的方法。您可以在最前面指定模式。

```bash
content/gallery/anygalleryname/index.md

---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
description: 
type: gallery
mode: one-by-one # at-once or one-by-one
tags:
-
series:
-
categories:
-
images: # when mode is one-by-one, images front-matter variable works
  - image: image1.jpg # image path: static/gallery/anygalleryname/image1.jpg
    caption: caption1
  - image: image2.jpg # image path: static/gallery/anygalleryname/image2.jpg
    caption: caption2
    ...
---

```

If you set the mode to one-by-one, the list.html page will use images front-matter variable you set above. If you set the mode to at-once, list.html page will not use front-matter images variable and just read all files under the static/gallery/anygalleryname folder.

1. Make a gallery folder under the content folder

```bash
root
├── content
│   ├── gallery
```

2. Make a sub folder under the gallery folder

```bash
root
├── content
│   ├── gallery
│   │   ├── anygalleryname
```

3. Make a index.md file under the sub folder using this command

```bash
hugo new --kind gallery gallery/anygalleryname/index.md
```

4. Put your images in static folder

```bash
root
├── static
│   ├── gallery
│   │   ├── anygalleryname
│   │   │   ├── ...your images here
```

## Contact Page

Currently available service: [formspree]. Open an issue if you need another service vendor. If you want just a blank page and use a markdown, set the service param empty.

1. Make a file at root/content/contact/index.md

```yaml
---
title: "Contact"
date: 2019-12-17T23:58:33+09:00
description: Contact page
type: contact
service: formspree
formId: "your@email.com"
---

This is contact page.
```

2. Add contact menu at root/config/_default/menus.en.toml.

```toml
...
[[main]]
  identifier = "contact"
  name = "contact"
  url = "contact"
  weight = 6
```

## Talks Page

Talks page is a listing page of links(video, ppt, event, ...). UI is similar to the archive page. Follow the below steps to make it.

1. Make a file at root/content/talks/_index.md.

```yaml
---
title: "Talks"
date: 2019-12-30T11:14:14+09:00
description: Talks Page
titleWrap: wrap # wrap, nowrap
---
```

2. Next, make some files under the `talks` folder you have created in step 1. If you want to make other link post, then make another file under the `talks` folder.

root/content/talks/myLinks.md

```yaml
---
title: "My Awesome links"
date: 2019-12-31T00:04:50+09:00
publishDate: 2019-12-31
description:
tags:
-
series:
-
categories:
-
---
```

3. Finally, make a menu at your root/config/_default/menus.en.toml file

```toml
[[main]]
  identifier = "talks"
  name = "talks"
  url = "talks"
  weight = 6
```

And we are good to go.

4. Additionally, if you want to use a future date for the talks page, you need more things to do.

    - add config variable named `buildFuture` at root/config/_default/config.toml

    ```toml
    ...
    buildFuture = true
    ...
    ```

    - add publishDate front matter to your md file at root/content/talks/myLinks.md

    ```yaml
    ---
    title:
    date:
    publishDate: 2020-02-20
    ...
    ---
    ...
    ```

## Showcase Page

Showcase page is a listing page of project showcase. Follow the below steps to make it.

1. Make a file at `root/content/showcase/_index.md`.

```yaml
---
title: "Showcase overview" # For SEO
date: 2020-01-19T15:43:38+09:00
description: My portfolio, repos, works overview page # For SEO
enableBio: true # Set to false if you want to hide the bio component.
---
```

2. Make a category folder and a file at `root/content/showcase/hugo/_index.md`. (In my case, hugo is a category)

```yaml
---
title: "Hugo" # category name
date: 2020-01-19T21:04:11+09:00
description: Hugo theme collection # For SEO
category: theme # meta info appeared on a card bottom side. category in category
enableBio: true
---
```

3. Make a file per project.

`root/content/showcase/hugo/my-awesome-project.md`.

```yaml
---
title: "My Awesome Project" # apperared on a card component
date: 2020-01-19T21:13:42+09:00
description: Hello world! This is my awesome project! # apperared on a card component
weight: 1 # card ordering
link: https://github.com/zzossig/hugo-theme-zzo
repo: https://github.com/zzossig/hugo-theme-zzo
pinned: true # appreared on a overview page.
thumb: feature3/css3.png # relative path in static/images
---
```

4. Finally, make a menu at your root/config/_default/menus.en.toml file

```toml
[[main]]
  identifier = "showcase"
  name = "Showcase"
  url = "showcase"
  weight = 7
```

## Multi Language

The default language of this theme is English. If you want to use another language, follow these steps

1. Make a menu file.

```bash 
root
├── config
│   ├── _default
│   │   ├── ...
│   │   ├── menus.ko.toml
```

```bash
config/_default/menus.ko.toml

[[main]]
  identifier = "about"
  name = "about"
  url = "/about/"
  weight = 1

[[main]]
    identifier = "archive"
    name = "archive"
    url = "/archive/"
    weight = 2
...
```

2. Make a content file. Add your language code before the md extension.

```bash
hugo new about/index.ko.md
hugo new posts/markdown-syntax.ko.md
...
```

3. Make an i18n file.

```bash
i18n/ko.toml

[search-placeholder]
other = "검색..."

[summary-dateformat]
other = "2006년 01월 02일"

[tags]
other = "태그"

...
```

4. Edit config.toml file.

```bash
defaultContentLanguage = "ko"
defaultContentLanguageInSubdir = true
hasCJKLanguage = true
```

## Customizing

It's a better idea not to modify the Zzo theme's folder if you want future support and upgrade. (You can modify if it doesn't matter) If you want more customizing options, open a new issue.

### custom css

1. Add this line of code to your params.toml file.

```bash
config/_default/params.toml

...
custom_css = ["css/custom.css", "scss/custom.scss", ...]
...
```

2. Add your file to assets folder. Filename must match with config params you set above.

```bash
assets/scss/custom.scss
assets/css/custom.css
```

3. If you want to modify the Zzo theme's default color, you should override the theme style. For example, if you're going to change the body background-color because I set the background-color in #body selector, not in the body tag selector, you should override body background-color there. Body tag selector won't work. And make sure to set !important. After setting the values, restart Hugo.

```css
assets/scss/custom.scss or assets/css/custom.css

...
#body {
  background-color: red !important;
}
...
```

### custom js

1. Add this line of code to your params.toml file.

```bash
config/_default/params.toml

...
custom_js = ["js/custom.js", ...]
...
```

2. Add your file to assets folder. Filename must match with config params you set above.

```bash
assets/js/custom.js
```

### custom syntax highlighting

1. Make a skin.toml file at root/data folder. Set the theme_dark_chroma, theme_light_chroma, ... params value as you want. Refer this [link](https://xyproto.github.io/splash/docs/all.html). If theme_[xxxx]_chroma value include - or _ like special character, just delete it.
For example, if you want use solarized-dark256 style, set the param like this.

```
root/data/skin.toml

theme_dark_chroma = "solarizeddark256"
```

2. Add a custom style file if you want to change specific colors. [[custom-css](#custom-css)]
Then, override chroma class. You can find this class at themes/zzo/assets/sass/syntax folder.
Example code is like this.

```
root/assets/scss/custom.scss

.chroma {
  background-color: #123456 !important;
}
```

Make sure that !important is necessary. After you changed this param, restart hugo.

### custom header

You may want to change home page header. There are 5 options which is slider, image, text, typewriter, empty.

1. Set param at config/_default/params.toml(homeHeaderType)

2. Make _index.md file at root/content/_index.md and copy & paste below.

```yaml
---
header:
- type: typewriter
    methods:
      - typeString: Hello world!
      - pauseFor: 2500
      - deleteAll: true
      - typeString: Strings can be removed
      - pauseFor: 2500
      - deleteChars: 7
      - typeString: <strong>altered!</strong>
      - pauseFor: 2500
    options:
      loop: true
      autoStart: false
    height: 190
    paddingX: 50
    align: center
    fontSize: 44
    fontColor: yellow

  - type: text
    height: 200
    paddingX: 50
    paddingY: 0
    align: center
    title:
      - HUGO
    subtitle:
      - The world’s fastest framework for building websites
    titleColor: # #123456, red
    titleShadow: false
    titleFontSize: 44
    subtitleColor: # #123456, red
    subtitleCursive: false
    subtitleFontSize: 16
    spaceBetweenTitleSubtitle: 20
  
  - type: img
    imageSrc: images/header/background.jpg # your image file path: root/static/images/header/background.jpg
    imageSize: cover # auto|length|cover|contain|initial|inherit
    imageRepeat: no-repeat # repeat|repeat-x|repeat-y|no-repeat|initial|inherit
    imagePosition: center # x% y%| xpos ypos| left top| center bottom| ...
    height: 235
    paddingX: 50
    paddingY: 0
    align: center
    title:
      -
    subtitle:
      -
    titleColor:
    titleShadow: false
    titleFontSize: 44
    subtitleColor:
    subtitleCursive: false
    subtitleFontSize: 16
    spaceBetweenTitleSubtitle: 20

  - type: slide
    height: 235
    options:
        startSlide: 0
        auto: 5000 # auto slide delay 5000ms(5sec)
        draggable: true # slide draggable
        autoRestart: true # restart after drag finished
        continuous: true # last to first
        disableScroll: true
        stopPropagation: true
    slide:
      - paddingX: 50
        paddingY: 0
        align: left
        imageSrc: images/header/background.jpg
        imageSize: cover
        imageRepeat: no-repeat
        imagePosition: center
        title:
          - header title1
        subtitle:
          - header subtitle1
        titleFontSize: 44
        subtitleFontSize: 16
        spaceBetweenTitleSubtitle: 20

      - paddingX: 50
        paddingY: 0
        align: center
        imageSrc: images/header/background.jpg
        imageSize: cover
        imageRepeat: no-repeat
        imagePosition: center
        title:
          - header title2
        subtitle:
          - header subtitle2
        titleFontSize: 44
        subtitleFontSize: 16
        spaceBetweenTitleSubtitle: 20

      - paddingX: 50
        paddingY: 0
        align: right
        imageSrc: images/header/background.jpg
        imageSize: cover
        imageRepeat: no-repeat
        imagePosition: center
        title:
          - header title3
        subtitle:
          - header subtitle3
        titleFontSize: 44
        subtitleFontSize: 16
        spaceBetweenTitleSubtitle: 20
---
```

3. Edit params as you wish.

### custom grid

1. Make a grid.toml file in data folder. (data/grid.toml)

2. Copy the contents of themes/zzo/data/grid.toml file and paste it into the grid.toml file you created above.

3. Change the grid as you want.

4. Once you change the grid.toml file, restart hugo.

```toml
data/grid.toml example

grid_max_width = "960"
grid_max_unit = "px" #  "px", "\"%\""  Using% is limited to using full width.
grid_main_main_width = "5"
grid_main_main_unit = "fr" # "fr", "px"
grid_main_side_width = "2"
grid_main_side_unit = "fr" # "fr", "px"
grid_column_gap_width = "32"
grid_column_gap_unit = "px" # "px"
grid_navbar_height = "50px" # "px"
grid_row_gap = "0"
```

### custom font

1. Add custom css file

```bash
config/_default/params.toml

...
custom_css = ["css/font.css"]
...
```

Set the above param and add file to assets/css/font.css

2. In your font.css file, add font-face something like this.

```css
@font-face {
    font-family: 'Montserrat';
    src: url('../fonts/montserrat-black.woff2') format('woff2'),
         url('../fonts/montserrat-black.woff') format('woff');
    font-weight: 900;
    font-style: normal;
}

@font-face {
    font-family: 'Merriweather';
    src: url('../fonts/merriweather-regular.woff2') format('woff2'),
         url('../fonts/merriweather-regular.woff') format('woff');
    font-weight: 400;
    font-style: normal;
}
```

3. Add your fonts file at root/static/fonts/myfont.xxx (If your url in step2 is ('../fonts/myfont.xxx')).

4. Make a font.toml file at root/data/font.toml and make variables as below.

```toml
title_font = "\"Montserrat\", sans-serif"
content_font = "\"Merriweather\", serif"
```

5. Another approach

Make a file at root/layouts/partials/head/custom-head.html and then load font style. 

```html
<link href="https://fonts.googleapis.com/css?family=Noto+Sans+KR:400,700&display=swap&subset=korean" rel="stylesheet">
```

### custom copyright

If you want to add a link to the footer copyright, not just a text, you can customize it.

1. In your config.toml file, set the copyright param like this.
```toml
...
copyright = This is my {} copyright text
...
```
The {} part will be your copyright link.
2. In your params.toml file, set the copyrightOptions params

```toml
...
[copyrightOptions]
  enableCopyrightLink = false
  copyrightLink = "https://..."
  copyrightLinkImage = "https://..."
  copyrightLinkText = "copyright link text"
```

### custom favicon

Override the default favicon by adding your favicon at root/static folder

## Author

We have some front matters for specifying the author.

```yaml
---
title:
...
author: # author name
authorEmoji: 🤖 # emoji for subtitle, summary meta data
authorImage: "/images/whoami/avatar.jpg" # image path in the static folder
authorImageUrl: "" # your image url. We use `authorImageUrl` first. If not set, we use `authorImage`.
authorDesc: # author description
socialOptions: # override params.toml file socialOptions
  email: ""
  facebook: ""
  ...
---
```

## Favicon

Put your `favicon.ico` file under the static folder. The filename should be `favicon` and the extension should be `ico`.

### Using favicon-genarator

If you want to support mobile favicon, use [favicon-generator](https://www.favicon-generator.org/).

- Make favicons from favicon-generator site.
- Make a folder at `root/static/favicon`
- Unzip the generated favicon to that folder.
- Set the config param `useFaviconGenerator` to `true`

## External Library

If you want use external libraries, this theme currently supporting Katex, MathJax, Mermaid, Flowchart.js, chart.js, viz-graph, wavedrom, js-sequence-diagram. Just add some variable to a front-matter.

```bash
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
...
libraries:
- katex 
- mathjax
- chart
- flowchartjs
- msc
- katex
- mermaid
- viz
- wavedrom
---

```
You can add some config option parameters at data/flowchartjs.json

## Shortcodes

### alert

```bash
{{< alert theme="warning" >}} # warning, success, info, danger
**this** is a text
{{< /alert >}}
```

### expand

```bash
{{< expand "Expand me" >}}Some Markdown Contents{{< /expand >}}
```

### img

```bash
// path: static/images/whoami/avatar.jpg
{{< img src="/images/whoami/avatar.jpg" title="Image4" caption="Image description" alt="image alt" width="50px" height="50px">}}
```

### notice

```bash
{{< notice success >}} # success, info, warning, error
success
{{< /notice >}}
```

### color

```bash
{{< color "#0000ff" >}}*text*{{< /color >}}
```

### box

```bash
{{< box >}}
Some contents
{{< /box >}}
```

### boxmd

```bash
{{< boxmd >}}
Some markdown contents
{{< /boxmd >}}
```

### code / codes => Tabbed code-block. indentation matters.

`````
{{< codes java javascript >}}
  {{< code >}}
  ```java
  System.out.println('Hello World!');
  ```
  {{< /code >}}
  {{< code >}}
  ```javascript
  console.log('Hello World!');
  ```
  {{< /code >}}
{{< /codes >}}
`````

### tab / tabs => Tabs make it easy to explore and switch between different views

⚠️Becareful that the content in the tab should be different from each other.
The tab makes unique id hashes depending on the tab contents.
So, If you just copy-paste the tabs with multiple times, since it has the same contents, the tab will not work.

`````
{{< tabs Windows MacOS Ubuntu >}}
  {{< tab >}}

  ### Windows section

  ```javascript
  console.log('Hello World!');
  ```

  {{< /tab >}}
  {{< tab >}}

  ### MacOS section

  Hello world!
  {{< /tab >}}
  {{< tab >}}

  ### Ubuntu section

  Great!
  {{< /tab >}}
{{< /tabs >}}
`````