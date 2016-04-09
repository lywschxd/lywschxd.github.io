# MdWiki 环境搭建

## mdwiki 环境
在github上下载编译好了的mdwiki，新建index.md, 默认寻找index.md。用firefox打开mdwiki.html,其他浏览器需要http server，这个时候就会显示index.md的内容。

## 基本配置
### 初始化配置 config.json
在mdwiki.html同级目录下新建config.json文件
```json
{
    "useSideMenu": true,
    "lineBreaks": "gfm",
    "title": "Dong's wiki"
}
```
**若没有这个文件，mdwiki会显示默认配置，同时报找不到config.json**

### 导航条
在mdwiki.html同级目录下新建navigation.md文件

###### 主题选择：
在[bootstrap](http://bootswatch.com/)下载css，放到mdwiki.html同级目录，然后再navigation.md文件中添加`[gimmick:theme](主题名)` 主题名是主题的名字不是css的名字

###### 导航条设置：
 一级菜单
```markdown
  # Your wiki name

  [Home](home.md)
  [About](about.md)
  [Download](download.md)
```
二级菜单
```markdown
  [Menu]()

  * #
  * [SubMenu Item 1](pages/index.md)
  * [SubMenu Item 2](pages/index.md)
  ----
  * #
  * [SubMenu Item 3](pages/index.md)
  * [SubMenu Item 4](pages/index.md)
```

###### 语法高亮：
mdwiki 对html和xml的语法高亮支持不好，会引起js


|Language|Keyword |
|-------|---------:|
|Bash|	bash|
|C#|	csharp|
|C++|	cpp|
|CSS|	css|
|CMake|	cmake|
|HTML|	html|
|HTTP|	http|
|Java|	java|
|JavaScript|	javascript|
|JSON|	json|
|Markdown|	markdown|
|Objective C|	objectivec|
|PHP|	php|
|Python|	python|
|SQL|	sql|
|XML|	xml|
