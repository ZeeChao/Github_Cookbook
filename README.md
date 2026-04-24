# Github_Cookbook

一份系统化的 GitHub 完整使用指南，涵盖从入门基础到进阶技巧的全面内容。无论你是初学者还是进阶用户，都能在这里找到实用的操作指南和最佳实践。

## 📚 内容导航

```
Github_Cookbook/
├── README.md
├── docs/
│   ├── github_basics.md                # GitHub 基础操作指南
│   │   └── 包含：注册登录、新建仓库、克隆、提交、分支、历史回退等基础操作
│   │
│   ├── repository_management.md        # 仓库管理与协作指南
│   │   └── 包含：设置、权限管理、分支保护、归档/删除、迁移重命名等
│   │
│   ├── issues_pr.md                    # Issue 与 Pull Request 流程
│   │   └── 包含：Issue 创建管理、PR 工作流、协作管理、自动化关联等
│   │
│   ├── actions_ci_cd.md                # GitHub Actions 与 CI/CD 指南
│   │   └── 包含：Workflow 基础、常用场景、触发器、Job 配置等
│   │
│   ├── security.md                     # 权限、安全与合规指南
│   │   └── 包含：认证方式、权限模型、安全最佳实践、合规配置等
│   │
│   ├── github_pages.md                 # GitHub Pages 网站搭建指南
│   │   └── 包含：Pages 配置、静态网站部署、自定义域名等
│   │
│   ├── tips_tricks.md                  # GitHub 进阶技巧与最佳实践
│   │   └── 包含：高级查询、快捷键、团队协作最佳实践等
│   │
│   └── workflow_templates/             # 工作流示例与模板
│       └── 包含：各类 CI/CD 工作流配置示例
│
├── examples/
│   ├── actions/                        # GitHub Actions 配置示例
│   │   └── 包含：多种常见的 Action 配置文件示例
│   │
│   ├── pages/                          # GitHub Pages 项目案例
│   │   └── 包含：Jekyll、Hugo、静态网站等示例
│   │
│   └── workflows/                      # CI/CD 工作流文件
│       └── 包含：测试、构建、部署等常用工作流
│
├── assets/
│   ├── images/                         # 配图、截图等素材
│   └── diagrams/                       # 操作流程、架构图等
│
└── LICENSE
```

## 🚀 快速开始

### 初学者路线
1. 从 [GitHub 基础操作指南](docs/github_basics.md) 开始，了解账户创建、仓库创建、代码提交等基础概念
2. 学习 [仓库管理指南](docs/repository_management.md)，掌握协作和权限设置
3. 深入 [Issue 与 PR 指南](docs/issues_pr.md)，理解协作开发流程

### 进阶学习路线
1. 了解 [GitHub Actions 与 CI/CD](docs/actions_ci_cd.md)，实现自动化工作流
2. 学习 [安全与合规](docs/security.md)，保护你的项目和数据
3. 探索 [GitHub Pages](docs/github_pages.md)，构建个人网站或文档站点
4. 掌握 [进阶技巧](docs/tips_tricks.md)，提升工作效率

## 📖 文档说明

### 文档结构特点

每份文档均按以下结构组织，确保内容清晰易懂：

- **引言**：简明扼要说明文档内容涵盖范围
- **目录**：快速导航到各个主要章节
- **Web UI 操作**：通过 GitHub 网页界面的操作步骤
- **命令行操作**：使用 Git 和 GitHub CLI 的命令示例
- **常见问题**：解答用户可能遇到的问题
- **参考资料**：链接到官方文档和相关资源

### 文档风格指南

- 所有操作说明都配有清晰的步骤编号
- 重要提示用引用块（`>`）标出
- 代码示例用代码块正确格式化
- 术语链接到定义或相关章节
- 每份文档以持续更新的承诺结尾

## 🎯 主要功能模块

### 1️⃣ GitHub 基础操作 (`github_basics.md`)
- 账户注册与登录
- 仓库创建与克隆
- 代码提交与推送
- 分支管理
- 提交历史查看与回退
- 常用术语解释

### 2️⃣ 仓库管理协作 (`repository_management.md`)
- 仓库设置和配置
- 成员权限管理
- 分支保护规则
- 仓库归档、删除、迁移
- 协作工作流

### 3️⃣ Issue 与 PR 工作流 (`issues_pr.md`)
- Issue 创建、管理、关闭
- Pull Request 发起与审核
- Issue 与 PR 关联
- 团队协作和代码审查
- 自动化工作流

### 4️⃣ GitHub Actions 与 CI/CD (`actions_ci_cd.md`)
- Workflow 基础概念
- Trigger（触发器）配置
- Job 和 Step 编写
- 常见自动化场景
- Workflow 调试技巧

### 5️⃣ 安全与合规 (`security.md`)
- 身份认证方式（SSH、Token）
- 权限模型和访问控制
- 安全最佳实践
- 敏感信息保护
- 组织级别合规配置

### 6️⃣ GitHub Pages (`github_pages.md`)
- Pages 启用与配置
- 静态网站部署
- 自定义域名
- 常见构建工具集成
- Pages 故障排查

### 7️⃣ 进阶技巧 (`tips_tricks.md`)
- 高级搜索和过滤
- 快捷键速记
- 团队协作最佳实践
- 工作流优化建议
- 常见陷阱和解决方案

## 💡 使用建议

- 📌 **循序渐进**：按照学习路线逐步掌握各个模块
- 🔄 **实践优先**：每学一个知识点都尝试在实际项目中应用
- 🤝 **参考官方文档**：本指南中的链接指向 GitHub 官方文档，遇到疑问时可深入查阅
- 💬 **积极反馈**：如发现文档错误或有改进建议，欢迎提交 Issue 或 PR

## 🛠️ 快速命令速记

### Git 基础命令
```bash
# 克隆仓库
git clone https://github.com/<用户名>/<仓库名>.git

# 提交代码
git add .
git commit -m "提交说明"
git push origin <分支名>

# 分支管理
git checkout -b <新分支名>
git branch
git checkout <分支名>

# 查看历史
git log --oneline
```

### GitHub CLI 常用命令
```bash
# 创建 Issue
gh issue create --title "问题标题" --body "描述"

# 创建 Pull Request
gh pr create --base main --head <分支名> --title "PR标题"

# 仓库操作
gh repo create <仓库名> --public
gh repo edit <owner>/<repo> --description "新描述"
```

## 📝 文档维护

本 Cookbook 持续保持更新以适应 GitHub 平台的最新变化。

- **更新时间**：定期检查并更新文档内容
- **贡献方式**：欢迎通过 Issue 和 PR 提出改进建议
- **问题反馈**：如发现文档过时或错误，请提交 Issue

## 📄 许可证

本项目采用 MIT License，详见 [LICENSE](LICENSE) 文件。

## 🔗 相关资源

- [GitHub 官方文档](https://docs.github.com/zh)
- [Git 官方教程](https://git-scm.com/book/zh/v2)
- [GitHub CLI 文档](https://cli.github.com/manual/)
- [Pro Git 中文版](https://git-scm.com/book/zh/v2)

---

**最后更新时间**：2026-04-24

> 🎓 无论你是 GitHub 新手还是进阶用户，这份 Cookbook 都将是你的得力助手。开始探索，持续学习，成为 GitHub 高手！
