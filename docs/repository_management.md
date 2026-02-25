# 仓库管理指南

> 本文档介绍在 GitHub 上通过 Web UI 和命令行两种方式进行仓库基本管理，包括设置、权限、协作、删除、归档等常见操作。

## 目录
- [仓库设置](#仓库设置)
  - Web UI 操作
  - 命令行操作
- [成员协作与权限管理](#成员协作与权限管理)
  - Web UI 操作
  - 命令行操作
- [分支保护管理](#分支保护管理)
  - Web UI 操作
  - 命令行操作
- [仓库归档和删除](#仓库归档和删除)
  - Web UI 操作
  - 命令行操作
- [仓库迁移和重命名](#仓库迁移和重命名)
- [常见问题与参考](#常见问题与参考)

---

## 仓库设置

### Web UI 操作

1. 打开你的仓库首页，点击上方 `Settings` 进入设置页。
2. 常见设置功能举例：
   - **修改仓库描述、README**：Settings > Repository name & Description。
   - **修改默认分支**：Settings > Branches > Default branch。
   - **添加标签（Topics）**：Settings > Repository details > Topics。
   - **设置仓库可见性**（公开/私有）：Settings > Danger Zone > Change repository visibility。
   - **设置仓库主页（README展示）**：编辑或新增 README.md 文件。
   - **启用/禁用 Issues、Wiki、Discussions**：Settings > Features。
   - **配置 Webhook/集成**：Settings > Webhooks 或 Integrations。

### 命令行操作

- 修改仓库远程地址（如改名或迁移后）：
  ```bash
  git remote set-url origin <新的仓库URL>
  ```
- 修改默认分支（需要使用 GitHub CLI 工具）：
  ```bash
  gh repo edit <owner>/<repo> --default-branch 新分支名
  ```
- 更改仓库描述（需 GitHub CLI）：
  ```bash
  gh repo edit <owner>/<repo> --description "新描述"
  ```
- 设置 topics（标签）（需 GitHub CLI）：
  ```bash
  gh repo edit <owner>/<repo> --add-topic topic1 --add-topic topic2
  ```
> **备注**：推荐安装 [GitHub CLI 工具（gh）](https://cli.github.com/) 以便在命令行下进行更多管理操作。

---

## 成员协作与权限管理

### Web UI 操作

1. 进入仓库 > Settings > Collaborators & teams（或“Manage access”）。
2. 点击 `Add collaborator`，输入对方的 GitHub 用户名，选择权限级别（Read、Triage、Write、Maintain、Admin）。
3. 邀请后，对方接受即可协作。
4. 可在同页移除成员或更改权限。

### 命令行操作

使用 GitHub CLI 增加协作者：

```bash
gh repo add-collaborator <owner>/<repo> <username> --permission write
```
移除协作者：
```bash
gh repo remove-collaborator <owner>/<repo> <username>
```
> 如果不用 CLI，可让协作者 fork 并通过 Pull Request 协作。

---

## 分支保护管理

### Web UI 操作

1. 进入仓库 > Settings > Branches。
2. 在 “Branch protection rules” 处点击 `Add rule`。
3. 填写分支名匹配规则（如: main），设定保护策略（如必须 Pull Request、CI 检查、代码审查、禁止强制推送等）。
4. 保存即可。

### 命令行操作

利用 GitHub CLI 工具：

```bash
gh api -X PUT \
  repos/<owner>/<repo>/branches/<branch>/protection \
  -f required_status_checks.strict=true \
  -f enforce_admins=true
```
> 详细参数可参考 [GitHub API 文档](https://docs.github.com/en/rest/branches/branch-protection)。

---

## 仓库归档和删除

### Web UI 操作

- **归档仓库**：
  1. 仓库首页 > Settings > General > Danger Zone。
  2. 找到 `Archive this repository`，点击并确认操作。
  3. 被归档仓库变为只读，无法继续操作代码和Issue。

- **删除仓库**：
  1. 仓库首页 > Settings > General > Danger Zone。
  2. 点击 `Delete this repository`，按要求输入仓库名并确认。

### 命令行操作

- **归档仓库**：
  ```bash
  gh repo archive <owner>/<repo>
  ```
- **取消归档**：
  ```bash
  gh repo unarchive <owner>/<repo>
  ```
- **删除仓库**（需确认，不可恢复）：
  ```bash
  gh repo delete <owner>/<repo>
  ```

---

## 仓库迁移和重命名

- **重命名仓库**：Web UI 下 Settings > Repository name 处直接修改，或者用 CLI:
    ```bash
    gh repo rename <owner>/<repo> 新名字
    ```
- **迁移仓库到新 owner**：Settings > Danger Zone > Transfer ownership，按照指引操作。
- **导出仓库所有内容**：Settings > Export repository。

---

## 常见问题与参考

- **协作者不能推送代码？**  
  需确认协作者权限为 Write 或更高。
- **Push 提示权限不足？**  
  检查 SSH/Token 配置及仓库权限设置。
- **删除/归档不可逆操作前请备份仓库！**

### 参考资料

- [GitHub 官方仓库设置说明](https://docs.github.com/zh/repositories/creating-and-managing-repositories)
- [GitHub CLI 官方文档](https://cli.github.com/manual/)
- [保护分支规则介绍](https://docs.github.com/zh/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/configuring-protected-branches)

---

> 本文档持续更新，建议结合项目具体需求优化仓库管理策略。
