# githubactions —— MkDocs 静态文档站

实验03 实践项目2：通过 GitHub Actions 自动部署静态文档到 GitHub Pages。

## 目录结构

```
githubactions/
├── docs/                       # Markdown 文档
│   ├── index.md                # 主页
│   ├── about.md                # 关于
│   ├── guide.md                # 使用指南
│   └── api.md                  # API 参考
├── .github/workflows/
│   └── deploy.yml              # 自动构建并部署到 gh-pages 的工作流
├── mkdocs.yml                  # MkDocs 配置（站点名、material 主题、导航）
└── README.md
```

## 本地预览

```bash
uv pip install --python .venv/Scripts/python.exe mkdocs-material
.venv/Scripts/python.exe -m mkdocs serve     # 打开 http://127.0.0.1:8000
```

只构建不预览：`.venv/Scripts/python.exe -m mkdocs build`，产物在 `site/`（已被 .gitignore 忽略）。

## 自动部署

推送到 `main` 分支且改动涉及 `docs/**` 或 `mkdocs.yml` 时，`deploy.yml` 会：

1. 检出代码、装 Python 3.9
2. `pip install mkdocs-material`
3. `mkdocs build` 生成 `site/`
4. 用 `JamesIves/github-pages-deploy-action@v4` 把 `site/` 推到 `gh-pages` 分支

站点地址：`https://zyt1113.github.io/githubactions/`
