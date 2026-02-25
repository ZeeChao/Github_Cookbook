# GitHub基础操作指南

> 本文档旨在帮助初学者快速掌握GitHub的基本使用方法，并提供常用操作流程参考。

## 目录
- [什么是GitHub](#什么是github)
- [注册与登录](#注册与登录)
- [仓库操作](#仓库操作)
  - [创建仓库](#创建仓库)
  - [克隆仓库](#克隆仓库)
  - [提交代码](#提交代码)
  - [查看历史与回退](#查看历史与回退)
- [分支管理](#分支管理)
- [协作基本操作](#协作基本操作)
- [常用术语](#常用术语)
- [参考资料](#参考资料)

---

## 什么是GitHub

GitHub 是基于 Git 的代码托管平台，支持版本管理、多人协作。它也是开源项目交流和发现的社区。

## 注册与登录

1. 访问 [github.com](https://github.com/)。
2. 点击 Sign up 注册账号，建议绑定邮箱用于接收通知。
3. 完成验证后可登录，配置个人资料。

## 仓库操作

### 创建仓库

- 登录后点击页面右上角的 "+" 选择 “New repository”。
- 填写仓库名称（如 `my-project`），可选择公开或私有。
- 可初始化 README、.gitignore 文件。

### 克隆仓库

在本地使用命令行：
```bash
git clone https://github.com/<用户名>/<仓库名>.git
```
或通过 SSH：
```bash
git clone git@github.com:<用户名>/<仓库名>.git
```

### 提交代码

1. 编辑/新增文件。
2. 添加到暂存区：
   ```bash
   git add 文件名
   ```
3. 提交到本地仓库：
   ```bash
   git commit -m "描述信息"
   ```
4. 推送到远程仓库：
   ```bash
   git push
   ```

### 查看历史与回退

- 查看提交记录：
  ```bash
  git log
  ```
- 回退到某个提交：
  ```bash
  git checkout <提交ID>
  ```

## 分支管理

- 创建新分支：
  ```bash
  git branch 新分支名
  ```
- 切换分支：
  ```bash
  git checkout 新分支名
  ```
- 合并分支：
  ```bash
  git merge 目标分支
  ```
- 删除分支：
  ```bash
  git branch -d 分支名
  ```

## 协作基本操作

- **Fork**：复制别人仓库到自己账户，适合参与开源项目。
- **Pull Request (PR)**：提交自己的代码更改到主仓库，协作讨论。
- **Issue**：提交问题、建议、讨论事项。
- **Review**：审查代码，建议改进。

## 常用术语

- **Repository（仓库）**：代码项目的集合。
- **Branch（分支）**：代码开发的不同线。
- **Commit（提交）**：代码更改的一次记录。
- **Merge（合并）**：把代码变更整合到主线。
- **Fork（派生）**：复制别人仓库到自己账户。
- **Pull Request（拉取请求）**：贡献代码时的申请。

## 参考资料

- [GitHub官方文档](https://docs.github.com/zh)
- [Pro Git 中文版](https://git-scm.com/book/zh/v2)
- [GitHub 教程 - 廖雪峰](https://www.liaoxuefeng.com/wiki/1016959663602400)
- [Git 入门指南](https://www.runoob.com/git/git-tutorial.html)

---

> 本文档可根据后续学习和项目需求扩展、补充，欢迎反馈与完善！
