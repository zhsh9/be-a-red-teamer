# Inventory

- [Inventory](#inventory)
- [Crash Course](#crash-course)
- [开发环境搭建](#开发环境搭建)
- [前置基础知识](#前置基础知识)
  - [HTML标签](#html标签)
  - [CSS基本写法](#css基本写法)

# Crash Course

- [ ] [PHP8快速入门在线教程](https://www.bilibili.com/video/BV1Xh411S7G1)
- [ ] [PHP从入门到精通](https://www.bilibili.com/video/BV16E411o7ko)
- [ ] [代码审计-php漏洞挖掘专题](https://www.bilibili.com/video/BV1kG411K7Ga)

# 开发环境搭建

- 服务器环境：PHPStudy
- 开发工具：PHPStorm, VSCode
- MySQL工具：Navicat, DataGrip
- 帮助文档：PHP手册，MySQL手册，W3CSchool手册

# 前置基础知识

- HTML
- CSS
- JavaScript

## HTML标签

- header
  - meta
    - \<meta charset="utf-8" /\>
    - \<meta name="Keywords" content="" /\>
    - \<meta name="Description" content="" /\>
  - title
  - linke
    - \<link type="text/css" rel="stylesheet" href="" /\>
    - \<link type="text/javascript" src="" /\>
- body
  - 文本标签
    - br, hr, p, i, em, b, strong, hn, sub, sup, del, font
  - 格式化标签
    - ul+li
    - ol+li
    - dl+dt+dd
    - div
    - span
  - 超链接标签
    - a
      - href
      - target
        - _blank
        - _parent
        - _self
        - _top
      - title
    - 锚点链接
  - 图片标签
    - img
      - src
      - alt
      - title
      - width
      - height
      - border
  - 多媒体标签
    - audio
      - src
      - controls
    - video
      - src
      - controls
      - loop
      - poster
  - 表格标签
    - table
      - caption
      - cellpadding
      - cellspacing
    - tr 行标签
    - th 头标签
    - td 列标签
    - colspan
    - rowspan
  - 表单标签
    - form
      - action 提交的目标地址
      - method 提交的方式(GET默认|POST)
      - enctype 提交内容的类型
        - application/x-www-form-urlencoded
        - multipart/form-data
        - text/plain
      - target 在何处打开目标URL
      - name 为属性表单起个名字，HTML5不支持用id替代
    - input
      - type
        - text
        - password
        - radio
        - checkbox
        - file
        - submit
        - reset
        - HTML5
          - date
          - time
          - url
          - email
          - number
      - value
      - readonly
    - select
      - option
    - textarea
  - button
  - fieldset
  - legend
  - optgroup
  - datalist
  - iframe

## CSS基本写法

selector {property: value}

- 选择器
  - 标签选择器, p
  - 类选择器, .class
  - id选择器, #id
  - 关联选择符
  - 组合选择符
  - 伪类选择符
    - :link，未访问
    - :visited，已访问
    - hover，鼠标悬停
    - active，激活的
- 属性
  - 颜色属性，color
  - 字体属性，font
    - font-size
    - font-family
    - font-style
      - normal
      - italic
      - oblique
    - font-weight
      - bold
      - light
  - 文本属性
    - text-indent
    - text-overflow
      - clip
      - ellipsis
    - white-space: nowrap
    - overflow
      - hidden
    - text-align
      - left
      - right
      - center
    - text-decoration
      - none
      - underline
      - line-through
    - text-shadow
    - letter-spacing
    - line-height
    - color
  - 边框
    - border
    - border-color
    - border-style
    - border-width
    - border-left-color
    - border-left-style
    - border-left-width
    - CSS3
      - border-radius
      - box-shadow
  - 背景属性，background
    - background-color
    - background-image
    - background-repeat
    - background-position
    - CSS3
      - background-size
      - background: url no-repeat scroll 10px 20px
      - background-origin: content-box, content-box
      - background-clip: padding-box, padding-box
      - background-size: 50px 60px, 50px 60px
  - 内补丁，padding
    - padding
    - padding-top, -bottom, -left, -right
  - 外补丁，margin
    - margin
    - margin-top, -bottom, -left, -right
  - 定位，position
    - position
      - absolute
      - fixed
    - z-index
    - top, bottom, left, right
- div+css布局

```
┌───────────────────────────────────────────────────────────────────────────┐
│                                                                           │
│                               margin-top                                  │
│                                                                           │
│      ┌────────────────────────────────────────────────────────────┐       │
│      │                        border-top                          │       │
│      │   ┌────────────────────────────────────────────────────┐   │       │
│      │   │                    padding-top                     │   │       │
│      │   │  ┌──▲───────────────────────────────────────────┐  │   │       │
│      │   │  │  │                                           │  │   │       │
│      │   │  │  │               Content                     │  │   │       │
│margin│   │  │  │                                           │  │   │margin │
│-left │   │  │  │                                           │  │   │-right │
│      │   │  │ height                                       │  │   │       │
│      │   │  │  │                                           │  │   │       │
│      │   │  │  │                width                      │  │   │       │
│      │   │  ◄──┴───────────────────────────────────────────►  │   │       │
│      │   │  └──▼───────────────────────────────────────────┘  │   │       │
│      │   │                   padding-bottom                   │   │       │
│      │   └────────────────────────────────────────────────────┘   │       │
│      │                       border-bottom                        │       │
│      └────────────────────────────────────────────────────────────┘       │
│                                                                           │
│                              margin-bottom                                │
│                                                                           │
└───────────────────────────────────────────────────────────────────────────┘
```

盒子模型

两种盒子（块和行内），特点是由CSS中的display属性决定的，
- Display:block  // 块盒子，自动占一行
- Display:inline // 行内盒子，一行摆放多个
