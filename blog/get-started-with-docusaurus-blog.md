---
title: Docusaurus 博客支持
authors: WheelsLab
tags: [docusaurus]
---
# Docusaurus 博客功能

Docusaurus 使用 [`@docusaurus/plugin-content-blog`](https://docusaurus.io/docs/api/plugins/@docusaurus/plugin-content-blog) 插件提供[博客功能](https://docusaurus.io/docs/blog)，`classic` 预设包含此插件，无须手动安装。

首先需要添加作者和文章的标签信息，用于在每篇博客的 Front Matter 中使用。
添加全局作者信息

+ `autherKey`：键名，用于在博客的 Front Matter 引用作者
  + `name`：姓名
  + `title`：职位/头衔
  + `url`：个人网址
  + `social`：社交账号
    + `github`
    + `x`

```yaml title="website/blog/authors.yml"
jmarcey:
  name: Joel Marcey
  title: Co-creator of Docusaurus 1
  url: https://github.com/JoelMarcey
  image_url: https://github.com/JoelMarcey.png
  email: jimarcey@gmail.com
  socials:
    x: joelmarcey
    github: JoelMarcey

slorber:
  name: Sébastien Lorber
  title: Docusaurus maintainer
  url: https://sebastienlorber.com
  image_url: https://github.com/slorber.png
  socials:
    x: sebastienlorber
    github: slorber
    email: seb@example.com
```

<!-- truncate -->

添加全局标签文件

```yaml title="blog/tags.yml"
releases:
  label: 'Product releases'
  permalink: '/product-releases'
  description: 'Content related to product releases.'

# A partial tag definition is also valid
announcements:
  label: 'Announcements'

# An empty tag definition is also valid
# Other attributes will be inferred from the key
emptyTag:
```

博客的 Front Matter，可以引用上面定义的作者和标签

```markdown
---
title: Welcome Docusaurus
authors:
  - slorber
  - yangshun
  - name: Joel Marcey
    title: Co-creator of Docusaurus 1
    url: https://github.com/JoelMarcey
    image_url: https://github.com/JoelMarcey.png
    socials:
      x: joelmarcey
      github: JoelMarcey
tags: [docusaurus]
description: This is my first post on Docusaurus.
image: https://i.imgur.com/mErPwqL.png
hide_table_of_contents: false
---

A Markdown blog post
```

博客列表页可以控制要显示的内容摘要，在文章中使用 `<!--truncate-->` 标记内容摘要，标记以上的内容将成为摘要

```markdown title="website/blog/my-post.md"
---
title: Markdown blog truncation example
---

All these will be part of the blog post summary.

<!-- highlight-next-line -->
<!-- truncate -->

But anything from here on down will not be.
```

:::note 
`mdx` 使用 `{/* truncate */}`
:::
