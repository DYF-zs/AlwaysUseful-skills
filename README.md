# AlwaysUseful Skills

**中文** | [English](./README_EN.md)

AlwaysUseful Skills 是一个用于整理、沉淀和复用 AI Skills 的仓库。

本仓库采用统一的 `skills/` 目录管理多个独立 skill。每个 skill 都应放在单独的子文件夹中，并至少包含一个 `SKILL.md` 文件。后续可以根据需要继续补充 README、示例、脚本、素材或其他辅助文件。

## 仓库结构

```text
AlwaysUseful-skills/
├── README.md
├── README_EN.md
├── .gitignore
└── skills/
    └── mdoc-present/
        ├── SKILL.md
        └── references/
            ├── design-tokens.md
            └── mermaid-setup.md
```

## Skills 列表

| Skill 名称      | 简介                                                       | 路径                    |
| --------------- | ---------------------------------------------------------- | ----------------------- |
| `mdoc-present`  | 将任意 Markdown 转换为自包含的规范化 HTML 演示页。         | `skills/mdoc-present/`  |

> 后续新增 skill 后，可以在这里继续补充对应名称、用途和路径。

## 安全提醒

请不要提交以下内容：

* API Key
* Token
* 密码
* `.env` 文件
* 私有配置文件
* 个人隐私信息
* 未脱敏的业务数据

如需提供配置示例，可以使用 `.env.example`，但不要包含真实密钥。

## License

This repository has not specified a license yet.
