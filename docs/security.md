# GitHub 仓库安全与权限管理指南

> 本文档介绍 GitHub 仓库的安全基础，包括权限设置、安全功能启用、常见安全操作的 Web UI 与命令行（CLI）方法。

## 目录
- [基础权限管理](#基础权限管理)
  - Web UI 操作
  - 命令行操作
- [代码保护与分支策略](#代码保护与分支策略)
  - Web UI 操作
  - 命令行操作
- [安全设置与自动化审查](#安全设置与自动化审查)
  - Web UI 操作
  - 命令行操作
- [安全建议与防护措施](#安全建议与防护措施)
- [参考资料](#参考资料)

---

## 基础权限管理

### Web UI 操作

1. 进入目标仓库 > `Settings` > `Manage access`。
2. Click `Invite a collaborator` 添加协作者，根据需求选择权限级别：Read、Triage、Write、Maintain 或 Admin。
3. 可随时调整协作者权限或移除成员。

### 命令行操作

需要 [GitHub CLI](https://cli.github.com/)：

- 添加协作者（指定权限）：
  ```bash
  gh repo add-collaborator <owner>/<repo> <username> --permission write
  ```
- 移除协作者：
  ```bash
  gh repo remove-collaborator <owner>/<repo> <username>
  ```
- 查看仓库协作者权限（需权限，部分功能需 API 支持）：
  ```bash
  gh api repos/<owner>/<repo>/collaborators
  ```

---

## 代码保护与分支策略

### Web UI 操作

1. 进入 `Settings` > `Branches`，在 “Branch protection rules” 区点击 `Add rule` 。
2. 设置受保护分支（如 main），可指定：
    - 必须经过 Pull Request
    - 必须通过 CI 测试绿灯
    - 必须审查通过数量
    - 禁止强制推送
    - 必须签名（Signed commits）等
3. 保存规则后，受保护的分支将强制遵循安全策略。

### 命令行操作

- 启用基本分支保护（需有管理员权限）
  ```bash
  gh api -X PUT repos/<owner>/<repo>/branches/<branch>/protection \
    -f required_status_checks.strict=true \
    -f enforce_admins=true
  ```
- 更多分支保护参数，可查 [官方 API 文档](https://docs.github.com/zh/rest/branches/branch-protection)。

---

## 安全设置与自动化审查

### Web UI 操作

1. 仓库 `Settings` > `Security` 或 `Code security and analysis`。
2. 可启用如下安全功能：
   - Dependabot Alerts（依赖漏洞预警）
   - Dependabot Security Updates（自动修复依赖漏洞）
   - Secret scanning（密钥与凭证扫描）
   - Code scanning（静态代码安全分析，可用内置或第三方工具）
   - 自动签名提交（Enforce signed commits）
3. 根据需要点击“Enable”激活相应功能，可查看已发现安全隐患结果和修复建议。

### 命令行操作

依赖于 GitHub CLI（部分功能需 API 操作或在 [高级设置文档](https://docs.github.com/zh/code-security)下用 REST API 实现）：

- 启用 Dependabot Alerts（API 示例）：
  ```bash
  gh api --method PATCH repos/<owner>/<repo> \
    -f security_and_analysis.dependabot_security_updates.status=enabled
  ```
- 查看 Dependabot 警报情况：
  ```bash
  gh api repos/<owner>/<repo>/dependabot/alerts
  ```
- 启用 code scanning，可通过提交带扫描的 workflow YAML、或用 CLI 上传 SARIF 文件：
  ```bash
  # 例如上传分析结果
  gh code-scanning upload --repo <owner>/<repo> analysis-results.sarif
  ```

---

## 安全建议与防护措施

- 开启两步验证（2FA）保护账号安全。
- 强制分支保护、防止直接向主分支推送代码。
- 启用依赖与代码自动安全扫描，按警告修复高危漏洞。
- 仓库设置中禁用“Allow force pushes”、“Allow deletions”以防止误操作。
- 避免将密码、Token 等敏感信息写入代码仓库；可启用 Secret scanning。
- 仅向受信任人员分配高级（Write/Admin）权限。

---

## 参考资料

- [GitHub 仓库权限管理](https://docs.github.com/zh/organizations/managing-access-to-your-organizations-repositories)
- [分支保护规则](https://docs.github.com/zh/repositories/configuring-branches-and-merges-in-your-repository/configuring-protected-branches)
- [GitHub 代码扫描和安全分析指南](https://docs.github.com/zh/code-security)
- [GitHub CLI 手册](https://cli.github.com/manual/)

---

> 持续关注仓库安全，定期审视访问权限和安全警报，保障团队和项目的安全！
