# Issue 与 Pull Request 操作指南

> 本文介绍在 GitHub 上使用 Issues 和 Pull Requests（PR，拉取请求）的基本流程，涵盖 Web UI 与命令行（CLI）两种方式，助你高效参与协作开发。

## 目录
- [Issue 基础操作](#issue-基础操作)
  - Web UI 操作
  - 命令行操作
- [Pull Request（PR）基础操作](#pull-requestpr基础操作)
  - Web UI 操作
  - 命令行操作
- [Issue & PR 的协作与管理](#issue--pr-的协作与管理)
  - 关联、分配、标签等
- [参考资料](#参考资料)

---

## Issue 基础操作

### Web UI 操作

1. 进入仓库主页，点击顶部 `Issues` 标签页。
2. 点击 `New issue` 创建新 Issue，填写标题和内容，必要时可以添加标签（Labels）、分配成员（Assignees）、指定里程碑（Milestone）、添加附件等。
3. 提交后可在 Issue 页面评论、关闭（Close）、重新打开（Reopen）；支持 Markdown 编辑。

### 命令行操作

使用 [GitHub CLI](https://cli.github.com/) 进行管理：

- 创建新 Issue
  ```bash
  gh issue create --title "你的问题标题" --body "详细描述"
  ```
- 查看 Issue 列表
  ```bash
  gh issue list
  ```
- 查看单个 Issue 详情
  ```bash
  gh issue view <issue编号>
  ```
- 评论 Issue
  ```bash
  gh issue comment <issue编号> --body "评论内容"
  ```
- 关闭 Issue
  ```bash
  gh issue close <issue编号>
  ```
- 重新打开 Issue
  ```bash
  gh issue reopen <issue编号>
  ```

---

## Pull Request(PR)基础操作

### Web UI 操作

1. 推送代码到你的分支后，进入仓库主页，点击 `Pull requests` 页签，再点 `New pull request`。
2. 选择 “compare” 分支与 “base” 分支，确认后填写 PR 标题与说明，可选择关联 Issue、添加标签、请求审查者(Reviewers)。
3. 提交后，PR 会展示分支差异、相关 Issue、CI 状态等，支持讨论和逐行代码评论。
4. 经审查通过可点击 `Merge` 按钮合并入主分支，亦可关闭（Close without merge）。

### 命令行操作

- 创建 Pull Request（以当前分支为例）
  ```bash
  # 先确保推送了当前分支到远程
  git push origin <your-branch>
  # 用 gh 发起 PR
  gh pr create --base main --head <your-branch> --title "PR 标题" --body "详细描述"
  ```
- 查看、列出 PR
  ```bash
  gh pr list
  gh pr view <PR编号>
  ```
- 评论 PR
  ```bash
  gh pr comment <PR编号> --body "评论内容"
  ```
- 合并 PR
  ```bash
  gh pr merge <PR编号>  # 可加 --merge --squash 或 --rebase 等参数
  ```
- 关闭 PR (不合并)
  ```bash
  gh pr close <PR编号>
  ```

---

## Issue & PR 的协作与管理

### 关联 Issue 与 PR

- 在 PR 描述或提交信息中加入关键词（如：`Closes #1`、`Fixes #1`），可在PR合并时自动关闭对应 Issue。
- 支持通过界面或命令行将 Issue 分配给协作者、添加标签/里程碑。

#### Web UI 操作
- 在 Issue 或 PR 页面右侧，添加 Assignees、Labels、Milestone。
- 在 PR 或 Issue 下方 “Linked issues” 处选择要关联的 Issue。

#### 命令行操作（部分需权限）
- 指定标签
  ```bash
  gh issue edit <issue编号> --add-label "bug"
  ```
- 指定负责人
  ```bash
  gh issue edit <issue编号> --assignee <username>
  gh pr edit <pr编号> --assignee <username>
  ```
- 关联 PR 与 Issue（可通过描述关键词，或用 [Projects/Automation](https://docs.github.com/zh/issues/trying-out-the-new-projects/automating-projects)）

---

## 参考资料

- [GitHub 官方 Issue 管理文档](https://docs.github.com/zh/issues/tracking-your-work-with-issues)
- [GitHub 官方 Pull Request 文档](https://docs.github.com/zh/pull-requests)
- [GitHub CLI 文档](https://cli.github.com/manual/)

---

> 实践中可根据团队要求自定义 Issue/PR 模板，保持讨论区高效有序。文档持续更新，欢迎完善和反馈！
