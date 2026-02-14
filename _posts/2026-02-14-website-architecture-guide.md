---
layout:     post
title:      "关于这个网站"
subtitle:   "给我自己看的此网站的技术架构与内容管理完整说明"
date:       2026-02-14
author:     "sapphire_fic的AI助理"
catalog:    true
tags:
    - 技术文档
    - 网站开发
    - 关于本站
---

## 网站架构

### 技术栈概述

原项目[Hux Blog](https://github.com/huxpro/huxpro.github.io)采用基于 Jekyll 的静态网站架构，结合现代前端技术栈构建而成：

| 技术/工具        | 版本/来源       | 用途               |
| ------------ | ----------- | ---------------- |
| Jekyll       | 静态网站生成器     | 生成静态HTML页面       |
| Bootstrap    | 前端框架        | 提供响应式布局和基础样式     |
| jQuery       | JavaScript库 | 简化DOM操作和事件处理     |
| Font Awesome | 图标库         | 提供网站所需的图标        |
| PWA          | 渐进式Web应用技术  | 实现离线访问、添加到主屏幕等功能 |
| Markdown     | 标记语言        | 编写博客文章           |
| Rouge        | 代码高亮器       | 实现代码块的语法高亮       |

### 目录结构

```
├── _includes/     # 可重用页面组件
│   ├── head.html          # 头部组件：元数据、资源引用、PWA配置
│   ├── nav.html           # 导航栏组件：网站导航，响应式设计
│   ├── footer.html        # 页脚组件：版权信息、脚本引用
│   ├── featured-tags.html # 特色标签组件
│   ├── intro-header.html  # 页面头部组件
│   └── search.html       # 搜索组件
├── _layouts/      # 页面布局模板
│   ├── default.html       # 默认布局：所有页面的基本结构
│   ├── post.html         # 文章布局：博客文章页面
│   ├── page.html         # 页面布局：独立页面
│   └── keynote.html      # 演示文稿布局
├── _posts/        # 博客文章（按日期和分类组织）
├── css/           # 样式文件
│   ├── bootstrap.css      # Bootstrap核心样式
│   └── hux-blog.css     # 自定义博客样式
├── js/            # JavaScript文件
│   ├── hux-blog.js       # 自定义主题JavaScript
│   ├── archive.js        # 归档页面脚本
│   └── jquery.tagcloud.js # 标签云效果
├── img/           # 图片资源
├── pwa/           # PWA相关文件
│   └── manifest.json     # Web应用清单
├── _config.yml    # 网站配置文件
├── about.html     # 关于页面
├── archive.html   # 文章归档页面
└── index.html     # 首页
```

### 组件构成

#### 页面组件模块

- **头部组件** (`head.html`)：包含网站元数据、资源引用、PWA配置，对SEO和页面渲染性能有重要影响
- **导航栏组件** (`nav.html`)：实现网站的导航功能，支持响应式设计和动画效果
- **页脚组件** (`footer.html`)：显示网站的版权信息、社交链接和其他辅助功能
- **侧边栏组件**：显示作者信息、标签云等
- **搜索组件** (`search.html`)：实现网站内容搜索功能
- **多语言选择组件**：支持中英文切换

#### 样式系统模块

- **Bootstrap核心样式**：提供基础样式和响应式网格系统
- **自定义博客样式** (`hux-blog.css`)：针对博客特点的自定义样式，包括侧边栏、目录、文章布局等

#### 脚本逻辑模块

- **导航栏交互**：实现导航栏的展开/折叠效果
- **搜索功能**：实现网站内容搜索
- **目录生成**：自动生成文章目录
- **PWA功能**：实现Service Worker注册和离线访问
- **多语言支持**：实现中英文切换功能
- **性能优化**：解决移动端300ms点击延迟问题

### 响应式设计实现

- **Bootstrap响应式网格系统**：提供基础响应式布局
- **媒体查询**：针对不同屏幕尺寸调整布局
- **响应式导航栏**：移动设备上折叠为汉堡菜单
- **图片响应式处理**：确保图片在不同设备上正确显示
- **字体大小调整**：使用相对单位，确保可读性

---

## 更新post的规范

### 文件命名规范

**格式**：`YYYY-MM-DD-标题.扩展名`

**示例**：

- `2026-02-14-my-first-post.md`
- `2026-02-14-learning-jekyll.markdown`

**注意事项**：

- 日期必须使用`YYYY-MM-DD`格式
- 标题使用小写字母和连字符，避免空格和特殊字符
- 扩展名可以是`.md`或`.markdown`

### Front Matter模板

每个post文件必须包含front matter，格式如下：

```yaml
---
layout:     post           # 必填：使用post布局
title:      "文章标题"       # 必填
subtitle:   "副标题"      # 可选
date:       2026-02-14     # 必填：发布日期
author:     "作者名"        # 可选
catalog:    true           # 可选：是否显示目录
header-style: text        # 可选：text或img
header-img: "img/xxx.jpg"  # header-style为img时必填
tags:                      # 可选：标签列表
    - 标签1
    - 标签2
mathjax:    false          # 可选：是否启用数学公式
multilingual: false        # 可选：是否启用多语言
---
```

### 创建新文章的完整流程

#### 步骤1：创建Markdown文件

在`_posts/`目录下创建符合命名规范的文件

#### 步骤2：编写front matter

复制上述模板，填写必要信息

#### 步骤3：编写文章内容

使用Markdown语法编写正文

#### 步骤4：本地预览（可选）

运行Jekyll服务器预览效果：

```bash
bundle exec jekyll serve
```

#### 步骤5：提交到GitHub

推送到GitHub仓库，GitHub Pages会自动构建

### 图片资源引用方式

**方式1：绝对路径（推荐）**

```markdown
![图片描述]({{ site.baseurl }}/img/post-bg.jpg)
```

**方式2：相对路径**

```markdown
![图片描述](/img/post-bg.jpg)
```

**图片存放位置**：

- 文章特定图片：`img/in-post/文章名/图片文件`
- 通用背景图片：`img/`目录下

### 标签系统使用

**添加标签**：在front matter中添加tags字段

```yaml
tags:
    - 技术文档
    - 网站开发
```

**标签显示规则**：

- 在`_config.yml`中配置：
  
  ```yaml
  featured-tags: true
  featured-condition-size: 1  # 文章数量大于此值的标签才会显示为特色标签
  ```

- Jekyll自动收集所有文章的标签到`site.tags`对象

- 标签会在归档页面和侧边栏自动显示

### 注意事项

1. **日期处理**：front matter中的date字段会覆盖文件名中的日期
2. **特殊字符**：标题中的中文需要正确编码，建议使用英文文件名
3. **图片路径**：确保图片路径正确，建议使用`{{ site.baseurl }}`前缀
4. **标签一致性**：标签名称大小写敏感，保持一致性
5. **代码高亮**：使用三个反引号包裹代码块，指定语言
6. **多语言支持**：如需多语言，在front matter中设置`multilingual: true`

### 文章排序规则

- 默认按日期降序排列（最新文章在前）
- 可以在`archive.html`中看到按年份分组显示
- 日期相同的文章按文件名字母顺序排列

---

## Post样例

以下是一个完整的post示例，包含所有必要元素和格式：

```markdown
---
layout:     post
title:      "我的第一篇博客文章"
subtitle:   "学习Jekyll与Markdown的入门指南"
date:       2026-02-14
author:     "徐拂来"
catalog:    true
header-style: text
tags:
    - 学习笔记
    - Jekyll
    - Markdown
---

## 引言

这是我使用Fly Blog发布的第一篇博客文章。本文将介绍如何使用Jekyll和Markdown创建和管理博客内容。

## 什么是Jekyll

Jekyll是一个简单的、博客感知的静态站点生成器。它将文本文件（如Markdown）转换为静态网站和博客。

### Jekyll的主要特点

- **静态网站**：生成的HTML文件可以直接部署，无需数据库
- **Markdown支持**：使用Markdown编写内容，简单易用
- **模板系统**：使用Liquid模板语言，灵活可扩展
- **GitHub Pages集成**：可以直接部署到GitHub Pages

## Markdown基础语法

### 标题

使用`#`号表示标题级别：

```markdown
# 一级标题
## 二级标题
### 三级标题
```

### 列表

无序列表：

```markdown
- 项目1
- 项目2
- 项目3
```

有序列表：

```markdown
1. 第一步
2. 第二步
3. 第三步
```

### 代码块

使用三个反引号包裹代码块：

```javascript
function hello() {
    console.log("Hello, World!");
}
```

### 链接和图片

链接：

```markdown
[链接文本](https://example.com)
```

图片：

```markdown
![图片描述](/img/example.jpg)
```

## 在Blog中发布文章

### 1. 创建新文件

在`_posts/`目录下创建新文件，命名格式为`YYYY-MM-DD-标题.md`

### 2. 编写Front Matter

```yaml
---
layout:     post
title:      "文章标题"
date:       2026-02-14
tags:
    - 标签1
    - 标签2
---
```

### 3. 编写内容

使用Markdown语法编写文章正文

### 4. 预览和发布

本地预览：

```bash
bundle exec jekyll serve
```

提交到GitHub：

```bash
git add .
git commit -m "Add new post"
git push
```

## 后记

本网站于2026.2.12建立。
