# site
值得玩维基

## Setup
```
hexo init site
cd site
git clone https://github.com/next-theme/hexo-theme-next themes/next
```

## Search
https://theme-next.js.org/docs/third-party-services/search-services
### installation
```
npm install hexo-generator-searchdb
```
### Hexo Config
```
search:
  path: search.xml
  field: post
  content: true
  format: html
```
### NexT Config
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

## Feed
https://github.com/hexojs/hexo-generator-feed
```
npm install --save hexo-generator-feed
```

# POSTs
hexo new page --path n1/index "斐讯N1"

# fa icon
https://fontawesome.com/v5.15/icons?d=gallery&p=2&m=free