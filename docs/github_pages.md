# GitHub Pages 网站搭建与管理指南

> 本文介绍如何在 GitHub 上启用 Pages 服务，用于构建、托管个人或项目网站，涵盖 Web UI 和命令行（CLI）两种操作方式。

## 目录
- [什么是 GitHub Pages](#什么是-github-pages)
- [启用 Pages 服务](#启用-pages服务)
  - Web UI 操作
  - 命令行操作
- [发布与更新网站内容](#发布与更新网站内容)
  - Web UI 操作
  - 命令行操作
- [自定义域名与 HTTPS 设置](#自定义域名与-https设置)
  - Web UI 操作
  - 命令行操作
- [常见问题与参考资料](#常见问题与参考资料)

---

## 什么是 GitHub Pages

GitHub Pages 是 GitHub 提供的免费静态网站托管服务，可以用于发表项目文档、个人主页、博客等。只需将 HTML、Markdown 或支持的框架代码推送到指定分支，GitHub 即自动发布网站。

---

## 启用 Pages 服务

### Web UI 操作

1. 进入你的仓库页面，点击 `Settings` > `Pages`（部分用户可能在 `Code and automation` 分类下）。
2. 在 “Build and deployment” 区，选择发布 source（如 `main` 分支上的 `/docs` 或 `root`）。
3. 点击 `Save`，页面下方会显示访问 URL（通常是 `https://<用户名>.github.io/<仓库名>/`）。
4. 若没有现成内容，可以先创建 `index.html` 或 `README.md` 作为首页文件。

### 命令行操作

1. 创建并添加网站内容文件：

    ```bash
    mkdir docs
    echo '<h1>Hello GitHub Pages</h1>' > docs/index.html
    git add docs/index.html
    git commit -m "添加 Pages 首页"
    git push
    ```

2. 切换分支并添加内容（如需发布到 `gh-pages` 分支）：

    ```bash
    git checkout --orphan gh-pages
    echo '<h1>My Project</h1>' > index.html
    git add index.html
    git commit -m "初始化 GitHub Pages"
    git push origin gh-pages
    ```

3. 使用 [GitHub CLI](https://cli.github.com/) 启动 Pages（部分 CLI 功能需配合 API 或 Web UI）：

    ```bash
    gh repo clone <owner>/<repo>
    gh api --method PATCH repos/<owner>/<repo> \
      -f pages.source.branch=main \
      -f pages.source.path="/docs"
    ```

---

## 发布与更新网站内容

### Web UI 操作

- 可以直接在 GitHub 网页端编辑或上传 `index.html`、Markdown 文件等，或新增/修改图片等资源。
- 每次保存或提交内容后，Pages 会自动构建与发布最新网站内容。

### 命令行操作

- 本地修改网站文件：

    ```bash
    echo '<p>新内容</p>' >> docs/index.html
    git add docs/index.html
    git commit -m "更新网站内容"
    git push
    ```

- 支持 Jekyll、Hugo、Hexo、VuePress 等主流静态网站生成器，编译后将输出目录推送到对应分支（如 `gh-pages`）。

---

## 自定义域名与 HTTPS 设置

### Web UI 操作

1. 在 `Settings > Pages` 下方 Custom domain 区，填写你的域名如 `www.example.com`，点击 `Save`。
2. 根据 GitHub 提示配置你的 DNS 记录（通常为 CNAME 指向 `username.github.io`），确保生效。
3. 勾选 `Enforce HTTPS`（强制 HTTPS），确保安全访问。

### 命令行操作

- 设置自定义域名（需 API 支持，部分需编辑 `CNAME` 文件）：

    ```bash
    echo "www.example.com" > docs/CNAME
    git add docs/CNAME
    git commit -m "添加自定义域名"
    git push
    ```

- 配合 [GitHub CLI](https://cli.github.com/) 或 REST API：

    ```bash
    gh api --method PATCH repos/<owner>/<repo> \
      -f pages.cname="www.example.com"
    ```

---

## 常见问题与参考资料

- **页面无法访问？**
  - 检查分支与目录是否正确；确认内容文件如 `index.html` 已推送；等待几分钟刷新。
- **自定义域名未生效？**
  - 检查 DNS 设置是否指向正确；查阅 GitHub Pages 官方文档。
- **自动部署失败？**
  - 检查 workflow log 或 repo settings 内 pages build 报错。
- **支持 HTTPS 吗？**
  - GitHub Pages 默认支持 HTTPS，且建议启用强制 HTTPS。

### 参考资料

- [GitHub Pages 官方文档](https://docs.github.com/zh/pages)
- [部署自定义域名/HTTPS 官方说明](https://docs.github.com/zh/pages/configuring-a-custom-domain-for-your-github-pages-site)
- [Jekyll 官方文档](https://jekyllrb.com/docs/)
- [GitHub Pages 故障和常见问题](https://docs.github.com/zh/pages/troubleshooting-pages)

---

> GitHub Pages 操作简单，支持多种框架与主题。建议结合项目需求选择发布方式，定期维护更新网站内容！
