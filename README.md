# 值得玩 软硬件 维基百科
欢迎各位软硬件爱好者！

这里会记录各种好玩的软件或者硬件，仅作为经验交流，文章或会有不足，希望大家能指正。网站的文章都能在[Github](https://github.com/zdwwiki/site)上提交pull request，大家也能参与。

## 网站设置

### 初始化hexo环境

#### 安装nodejs

https://nodejs.org/en/

#### 安装hexo

```
npm install hexo-cli -g
```

### 初始化项目

执行以下命令

```
hexo init site
cd site
git clone https://github.com/next-theme/hexo-theme-next themes/next
```

### 配置插件

#### 搜索插件

详情： https://theme-next.js.org/docs/third-party-services/search-services

##### Installation

```
npm install hexo-generator-searchdb
```

##### Hexo config

```
search:
  path: search.xml
  field: post
  content: true
  format: html
```

##### NexT config

```
# Local search
# Dependencies: https://github.com/next-theme/hexo-generator-searchdb
local_search:
  enable: true
  # If auto, trigger search by changing input.
  # If manual, trigger search by pressing enter key or search button.
  trigger: auto
  # Show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # Unescape html strings to the readable one.
  unescape: false
  # Preload the search data when the page loads.
  preload: false
```

#### 订阅插件

详情：https://github.com/hexojs/hexo-generator-feed

##### Installation

```
npm install --save hexo-generator-feed
```

##### Hexo config

```
# Feed
feed:
  type:
    - atom
    - rss2
  path:
    - atom.xml
    - rss2.xml
```

##### NexT config

```
social:
  RSS: /atom.xml || fa fa-rss
```

## 常用命令

初始化文章并指定目录

```
hexo new page --path phicomm/index "斐讯"
```

## 附录

查找font awesome图标：https://fontawesome.com/v5.15/icons?d=gallery&p=2&m=free

