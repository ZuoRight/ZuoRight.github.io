[ZuoRight](http://zuoright.com)

```python
pip install mkdocs
pip install mkdocs-material
pip install mkdocs-git-revision-date-localized-plugin
```

```yaml
site_name: site_name
site_description: site_description
site_author: 7c
site_url: http://zuoright.com

# repo_name: squidfunk/mkdocs-material
# repo_url: https://github.com/squidfunk/mkdocs-material

copyright: Copyright &copy; 2016 ~ Forever 7c

theme:
  name: material
  language: zh
  palette:
    scheme: slate
    primary: deep orange
    accent: indigo
  font:
    text: Roboto
    code: Roboto Mono
  icon:
    logo: material/guy-fawkes-mask
    # repo: material/source-branch
  favicon: images/favicon.png

extra:
  # 右下角社交图标和链接
  social:
    - icon: material/github
      link: https://github.com/ZuoRight
    - icon: material/email
      link: mailto:zuoright@foxmail.com
    - icon: material/home
      link: http://zuoright.com

markdown_extensions:
  - meta  # 可以添加元信息
  - admonition  # 可以添加提示条
  - codehilite:  # 代码高亮
      linenums: true  # 显示行号
      guess_lang: false
  - pymdownx.tabbed  # 分组式代码块
  - pymdownx.superfences

  - toc:
      permalink: true  # 固定链接

plugins:
  - search:
      lang:
        - ja
  - git-revision-date-localized:  # 文章底部显示更新时间，需要先安装插件
      type: iso_date
```