# GitHub Actions 与 CI/CD 入门指南

> 本文介绍如何在 GitHub 上利用 Actions 实现自动化、持续集成与持续部署（CI/CD），涵盖 Web UI 和命令行（CLI）两种操作方式。

## 目录
- [什么是 GitHub Actions](#什么是-github-actions)
- [快速开始](#快速开始)
  - Web UI 操作
  - 命令行操作
- [常见 CI/CD 场景实例](#常见-cicd-场景实例)
  - 构建与测试
  - 自动部署
- [管理和调试工作流](#管理和调试工作流)
  - Web UI 操作
  - 命令行操作
- [参考资料](#参考资料)

---

## 什么是 GitHub Actions

GitHub Actions 是 GitHub 提供的自动化引擎，支持基于事件触发的自动构建、测试与部署等流水线，广泛用于 CI/CD（持续集成/持续部署）和开发运维自动化场景。

---

## 快速开始

### Web UI 操作

1. 进入仓库，点击顶部 `Actions`。
2. 可选择官方推荐模板（如 Node.js、Python、Java、部署相关等），或点击 `set up a workflow yourself` 创建 `.github/workflows` 目录下的 YAML 工作流文件（如 `ci.yml`）。
3. 编辑 YAML 文件，例：

    ```yaml
    name: CI Demo

    on: [push, pull_request]

    jobs:
      build:
        runs-on: ubuntu-latest

        steps:
        - uses: actions/checkout@v4
        - name: Set up Node.js
          uses: actions/setup-node@v4
          with:
            node-version: '18'
        - run: npm install
        - run: npm test
    ```

4. 保存后工作流将自动启动并在每次 `push` 或 PR 时运行。

### 命令行操作

1. 手动在本地创建 `.github/workflows/ci.yml`：

    ```bash
    mkdir -p .github/workflows
    touch .github/workflows/ci.yml
    # 用编辑器填写内容
    ```

2. 编写 YAML 后推送到远程仓库：

    ```bash
    git add .github/workflows/ci.yml
    git commit -m "添加基本CI工作流"
    git push
    ```

3. 使用 [GitHub CLI](https://cli.github.com/)（需 2.0+）可列出与运行工作流：

    ```bash
    gh workflow list
    gh workflow run <workflow名>
    ```

---

## 常见 CI/CD 场景实例

### 构建与测试

#### Node.js 项目示例

```yaml
name: Node.js CI

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '16'
      - run: npm install
      - run: npm run build
      - run: npm test
```

#### Python 项目示例

```yaml
name: Python CI

on: [pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: '3.10'
      - run: pip install -r requirements.txt
      - run: pytest
```

### 自动部署

以部署静态网站到 GitHub Pages 为例：

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4
      - name: Build static site
        run: |
          npm install
          npm run build
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v4
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

---

## 管理和调试工作流

### Web UI 操作

- 查看运行结果：进入仓库 `Actions`，点击每次 workflow 运行可查看详细日志、执行步骤和错误。
- 重新运行/取消任务：点击运行页面右上角 `Re-run jobs` 或 `Cancel workflow run`。
- 禁用/启用工作流：进入目标 workflow 文件页，可选择 disable/enable。
- 编辑或删除 workflow：Actions 页面找到对应 workflow 旁的“三点”菜单可直接进行。

### 命令行操作

- 查看 workflow 列表和状态：

    ```bash
    gh workflow list
    gh run list
    ```

- 查看单次运行日志：

    ```bash
    gh run view <运行ID> --log
    ```

- 重新运行 workflow：

    ```bash
    gh workflow run <workflow名>
    ```

- 手动触发、取消或删除 workflow[s]：

    ```bash
    gh run cancel <运行ID>
    gh workflow disable <workflow名>
    gh workflow enable <workflow名>
    ```

---

## 参考资料

- [GitHub Actions 官方文档](https://docs.github.com/zh/actions)
- [官方市场工作流模板](https://github.com/marketplace?type=actions)
- [GitHub CLI（gh）Workflow管理](https://cli.github.com/manual/gh_workflow)

---

> Actions 支持丰富的社区生态，可按需自定义工作流，实现自动测试、打包、发布、部署等多场景自动化需求。建议结合实践持续优化与完善！
