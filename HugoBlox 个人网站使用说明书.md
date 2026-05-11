# HugoBlox 个人网站使用说明书

> 基于你的 GitHub Pages 项目 `zhu-wenbin.github.io` 的完整修改指南

---

## 📁 目录结构一览

```
zhu-wenbin.github.io/
├── config/_default/          # 🔧 配置文件目录
│   ├── hugo.yaml            # 基础配置
│   ├── params.yaml          # 🔥 主题、颜色、字体等核心设置
│   ├── menus.yaml           # 导航菜单配置
│   ├── languages.yaml       # 多语言设置
│   └── module.yaml          # 模块配置
│
├── content/                  # 📝 网站内容（最重要！）
│   ├── _index.md            # 首页布局和内容
│   ├── experience.md        # 经历页面
│   ├── authors/             # 作者信息
│   │   └── me.yaml          # 👤 你的个人信息（关键！）
│   ├── blog/                # 博客文章
│   ├── projects/            # 项目展示
│   ├── publications/        # 发表论文
│   └── events/              # 演讲/活动
│
├── data/                     # 📊 数据文件
│   └── authors/
│       └── me.yaml          # 作者详细资料（工作经历、教育、技能等）
│
├── assets/                   # 🎨 资源文件
│   └── media/               # 图片、视频等媒体文件
│
├── static/                   # 📦 静态文件（直接可访问）
│   └── uploads/             # 上传的文件（如 PDF 简历）
│
├── hugoblox.yaml            # 构建配置
└── README.md                # 项目说明
```

---

## 🚀 快速开始：三步修改网站

### 第一步：修改你的个人信息

**文件位置**：`data/authors/me.yaml`

这是最重要的文件！包含你的所有个人资料：# 基本信息修改

name:
  display: 朱文彬              # 修改为你的名字
  given: 文彬                  # 名
  family: 朱                   # 姓
  alternate: ''               # 英文名或其他别名
  pronouns: he/him            # 代词

# 状态图标
status:
  icon: "🚀"                  # 可以改成任何 emoji
  role: 学生 / 开发者          # 你的角色

# 个人简介
bio: |
  我是一名热爱技术的开发者，专注于...
  这里写一段简短的自我介绍

# 所属机构
affiliations:
  - name: 你的大学/公司
    url: https://example.com/

# 社交链接
links:
  - icon: at-symbol
    url: mailto:your-email@example.com  # 改成你的邮箱
    label: Email
  - icon: brands/github
    url: https://github.com/zhu-wenbin   # 改成你的 GitHub
  - icon: brands/linkedin
    url: https://linkedin.com/in/yourname

**可用的图标类型**：

- `at-symbol` - 邮箱
- `brands/github` - GitHub
- `brands/linkedin` - LinkedIn
- `brands/x` - Twitter/X
- `academicons/google-scholar` - Google Scholar
- `academicons/orcid` - ORCID

### 第二步：修改网站基本设置

**文件位置**：`config/_default/params.yaml`

```yaml
hugoblox:
  identity:
    name: "朱文彬"              # 网站名称
    tagline: "个人主页"        # 标语
    description: "朱文彬的个人网站"

  theme:
    mode: system               # light / dark / system（跟随系统）
    pack: "default"            # 主题包

    colors:
      primary: "blue"          # 主色调：blue, green, purple, red 等
      secondary: ""            # 次要颜色

  header:
    search: true               # 启用搜索功能
    theme_toggle: true         # 显示主题切换按钮
```

**可用的颜色**：

- `blue`, `indigo`, `purple`, `pink`, `red`
- `orange`, `yellow`, `green`, `teal`, `cyan`
- `gray`, `slate`, `zinc`, `neutral`
- 或使用十六进制：`"#6366f1"`

### 第三步：修改网站 URL

**文件位置**：`config/_default/hugo.yaml`

```yaml
baseURL: 'https://zhu-wenbin.github.io/'  # 改成你的网站地址
```

---

## 📝 修改页面内容

### 修改首页

**文件**：`content/_index.md`

```yaml
sections:
  # 个人简介部分
  - block: resume-biography-3
    content:
      username: me                    # 关联 data/authors/me.yaml
      button:
        text: 下载简历               # 按钮文字
        url: uploads/resume.pdf      # 简历文件路径

  # 自定义文本部分
  - block: markdown
    content:
      title: '👋 欢迎'
      text: |-
        这里写你的欢迎词...

  # 最新博客部分
  - block: collection
    id: news
    content:
      title: 最新动态
      count: 5                       # 显示数量
```

### 添加博客文章

在 `content/blog/` 目录下创建新文件：

**文件**：`content/blog/my-first-post.md`

```markdown
---
title: '我的第一篇博客'
date: 2026-05-09
summary: '这是文章摘要'
authors:
  - me
tags:
  - 技术
  - 学习
---

# 正文内容

这里写你的博客内容...

## 小标题

更多内容...
```

### 添加项目展示

在 `content/projects/` 目录下创建新文件：

**文件**：`content/projects/my-project.md`

```markdown
---
title: '我的项目'
summary: '项目简介'
date: 2026-05-09
tags:
  - Web开发
image:
  filename: project-preview.jpg
---

项目介绍...

## 技术栈

- HTML/CSS
- JavaScript
```

---

## 🎨 自定义外观

### 更换头像

1. 将你的头像图片放到 `assets/media/` 目录
2. 修改 `data/authors/me.yaml`：

```yaml
avatar:
  filename: "your-avatar.jpg"  # 图片文件名
```

### 添加简历 PDF

1. 将 PDF 文件放到 `static/uploads/` 目录
2. 确保文件名为 `resume.pdf`，或在 `content/_index.md` 中修改按钮链接

---

## 📋 修改导航菜单

**文件**：`config/_default/menus.yaml`

```yaml
main:
  - name: 首页
    url: /
    weight: 10
  - name: 经历
    url: /experience
    weight: 20
  - name: 项目
    url: /projects
    weight: 30
  - name: 博客
    url: /blog
    weight: 40
```

---

## 🛠️ 本地预览（推荐）

修改文件后，可以在本地预览效果：

### 安装 Hugo

```bash
# Windows (使用 Winget)
winget install Hugo.Hugo

# Mac (使用 Homebrew)
brew install hugo

# Linux
sudo apt-get install hugo
```

### 启动本地服务器

```bash
# 进入项目目录
cd d:/Viral_Code/2026.5.9_zhu-wenbin.github.io/zhu-wenbin.github.io

# 启动开发服务器
hugo server

# 或者指定端口
hugo server --port 1313
```

然后在浏览器打开：`http://localhost:1313`

---

## 🚢 部署到 GitHub Pages

### 方法一：直接推送到 GitHub（自动部署）

```bash
# 进入项目目录
cd d:/Viral_Code/2026.5.9_zhu-wenbin.github.io/zhu-wenbin.github.io

# 查看当前状态
git status

# 添加所有修改
git add .

# 提交
git commit -m "更新个人信息"

# 推送
git push
```

等待 2-5 分钟，访问 `https://zhu-wenbin.github.io/` 查看更新！

### 方法二：手动构建

```bash
# 构建网站
hugo

# 生成的静态文件在 public/ 目录
# 将 public/ 目录内容推送到 GitHub Pages 仓库
```

---

## 📊 常见修改场景


| 你想改什么         | 修改文件                      | 位置            |
| ------------------ | ----------------------------- | --------------- |
| 改名字、头像、简介 | `data/authors/me.yaml`        | 个人信息        |
| 改网站颜色         | `config/_default/params.yaml` | theme.colors    |
| 改网站标题         | `config/_default/params.yaml` | identity.name   |
| 添加工作经历       | `data/authors/me.yaml`        | experience 部分 |
| 添加教育背景       | `data/authors/me.yaml`        | education 部分  |
| 添加技能           | `data/authors/me.yaml`        | skills 部分     |
| 写博客             | `content/blog/` 目录          | 新建 .md 文件   |
| 添加项目           | `content/projects/` 目录      | 新建 .md 文件   |
| 改导航菜单         | `config/_default/menus.yaml`  | 菜单配置        |
| 改首页布局         | `content/_index.md`           | sections 配置   |

---

## 💡 技能等级设置

在 `data/authors/me.yaml` 中：

```yaml
skills:
  - name: 编程语言
    items:
      - label: Python
        level: 5          # 1-5 级，5 为最高
      - label: JavaScript
        level: 4
```

---

## 🔗 社交链接完整示例

```yaml
links:
  - icon: at-symbol
    url: mailto:your@email.com
    label: Email
  - icon: brands/github
    url: https://github.com/zhu-wenbin
    label: GitHub
  - icon: brands/linkedin
    url: https://linkedin.com/in/yourname
    label: LinkedIn
  - icon: brands/x
    url: https://twitter.com/yourname
    label: Twitter
  - icon: brands/weibo
    url: https://weibo.com/yourname
    label: 微博
  - icon: brands/bilibili
    url: https://space.bilibili.com/yourid
    label: B站
```

---

## ❓ 常见问题

### Q: 修改后网站没变化？

A: 可能需要清除浏览器缓存，或等待 GitHub Pages 重新部署（2-5分钟）

### Q: 本地预览报错？

A: 确保 Hugo 版本 >= 0.161.1，运行 `hugo version` 检查

### Q: 图片显示不出来？

A: 检查图片路径是否正确，推荐放在 `assets/media/` 目录

### Q: 如何添加中文支持？

A: 在 `config/_default/hugo.yaml` 中设置 `hasCJKLanguage: true`

---

## 📚 推荐学习资源

- [HugoBlox 官方文档](https://docs.hugoblox.com/)
- [Hugo 官方文档](https://gohugo.io/documentation/)
- [YAML 语法指南](https://learnxinyminutes.com/docs/yaml/)
- [Markdown 语法指南](https://www.markdownguide.org/)

---

## 🎯 下一步建议

1. ✅ 先修改 `data/authors/me.yaml` 填写你的基本信息
2. ✅ 修改 `config/_default/params.yaml` 选择你喜欢的颜色
3. ✅ 运行 `hugo server` 本地预览效果
4. ✅ 满意后 `git add . && git commit -m "更新网站" && git push`
5. ✅ 访问你的网站查看最终效果！

---

**祝你打造出完美的个人网站！** 🎉
