# GitHub 基础操作指南

> 本文档系统介绍 GitHub 的基础用法，涵盖 Web UI 界面和命令行两种常用操作方式，帮助你快速上手代码托管与协作。

## 目录
- [注册与登录](#注册与登录)
  - Web UI 操作
- [新建仓库](#新建仓库)
  - Web UI 操作
  - 命令行操作
- [克隆仓库](#克隆仓库)
  - Web UI 操作
  - 命令行操作
- [提交和推送代码](#提交和推送代码)
  - Web UI 操作
  - 命令行操作
- [分支管理](#分支管理)
  - Web UI 操作
  - 命令行操作
- [历史查看与回退](#历史查看与回退)
  - Web UI 操作
  - 命令行操作
- [常见术语](#常见术语)
- [参考资料](#参考资料)

---

## 注册与登录

### Web UI 操作

1. 打开 [github.com](https://github.com/)，点击右上角 `Sign up` 注册新账户。
2. 输入邮箱、用户名、密码，根据引导完成注册与邮箱验证。
3. 注册后可点击右上角 `Sign in` 登录。

---

## 新建仓库

### Web UI 操作

1. 登录 GitHub 后，点击右上角 “+” > `New repository`。
2. 填写仓库名、描述，选择公开/私有，并可勾选初始化 README 文件、添加 .gitignore 等，点击 `Create repository` 完成新建。

### 命令行操作

使用 [GitHub CLI](https://cli.github.com/) 新建仓库（需已全局配置 gh 并登录）：

```bash
gh repo create <仓库名> --public          # 创建公开仓库
gh repo create <仓库名> --private         # 创建私有仓库
```

---

## 克隆仓库

### Web UI 操作

1. 进入目标仓库页面，点击 `<> Code` 按钮，选择 `HTTPS` 或 `SSH` 复制地址。
2. 在本地执行克隆。

### 命令行操作

```bash
git clone https://github.com/<用户名>/<仓库名>.git
# 或 SSH 方式（需配置 SSH Key）
git clone git@github.com:<用户名>/<仓库名>.git
```

---

## 提交和推送代码

### Web UI 操作

1. 进入仓库页面，点击 `Add file` > `Create new file` 或上传文件。
2. 编辑内容后输入 commit message，点击 `Commit changes`。
3. 也可以在线修改、删除文件，操作后均有 commit 记录。

### 命令行操作

```bash
cd <仓库目录>
# 新增或修改文件
git add <文件名>
git commit -m "提交说明"
git push origin <分支名>      # 推送到远程分支（如 main）
```

---

## 分支管理

### Web UI 操作

1. 仓库页左上角点击当前分支名，下拉框点 `Create branch: <新分支名>` 新建分支。
2. 可以选择新分支为基础进行代码更改。
3. 可在 Pull requests 页提交分支合并请求。

### 命令行操作

```bash
# 新建分支
git checkout -b <新分支名>
# 查看本地分支
git branch
# 切换分支
git checkout <分支名>
# 推送分支到远程
git push origin <分支名>
```

---

## 历史查看与回退

### Web UI 操作

1. 进入仓库，点击 `Commits` 查看提交历史。
2. 可点击某个 commit 查看更改内容和文件差异。
3. 不同分支的历史可切换 branch 后查看。

### 命令行操作

```bash
# 查看提交历史
git log
# 可加 --oneline 简化输出
git log --oneline

# 回退到上一个提交（保留更改为未暂存状态）
git reset HEAD~1

# 恢复指定文件为上一个 commit 状态
git checkout <commit_id> -- <文件名>
```

---

## 常见术语

- **Repository**（仓库）：项目代码和版本管理的容器。
- **Branch**（分支）：独立进行开发、测试的线索。
- **Commit**（提交）：一次代码和更改的保存记录。
- **Clone**（克隆）：将远程仓库复制到本地。
- **Push**（推送）：将本地提交同步到远程仓库。
- **Pull**（拉取）：拉取远程仓库的更改到本地。
- **Merge**（合并）：将其他分支的更改合并到当前分支。
- **Pull Request (PR)**：请求将分支更改合入主分支，便于协作。

---

## 参考资料

- [GitHub 官方帮助文档](https://docs.github.com/zh)
- [廖雪峰的 Git 教程](https://www.liaoxuefeng.com/wiki/896043488029600)
- [Pro Git 中文版](https://git-scm.com/book/zh/v2)

---

> 建议每日实操练习，并结合具体项目逐步掌握更多进阶用法。文档持续更新，欢迎完善和反馈！
