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

## 单个 Skill 的推荐结构

```text
skill-name/
├── SKILL.md
├── README.md
├── examples/
├── assets/
└── scripts/
```

其中：

* `SKILL.md`：skill 的核心说明文件。
* `README.md`：该 skill 的独立介绍，可选。
* `examples/`：示例输入、示例输出或使用案例，可选。
* `assets/`：图片、模板、参考文件等素材，可选。
* `scripts/`：辅助脚本，可选。

## 如何新增一个 Skill

在 `skills/` 目录下创建新的 skill 文件夹：

```bash
mkdir skills/new-skill-name
touch skills/new-skill-name/SKILL.md
```

然后编辑 `SKILL.md`，补充该 skill 的用途、使用方式、输入输出要求和注意事项。

新增完成后，更新本 README 中的 Skills 列表，并提交到 GitHub：

```bash
git add .
git commit -m "Add new skill"
git push
```

## 维护规范

为了方便长期维护，建议遵循以下规范：

1. 一个 skill 对应一个独立文件夹。
2. 每个 skill 至少包含一个 `SKILL.md`。
3. 文件夹名称尽量使用英文小写和短横线，例如 `document-analysis`。
4. 不同 skill 之间尽量保持独立，避免互相依赖。
5. 示例、素材、脚本等辅助文件应放在对应 skill 的文件夹内。
6. 新增或修改 skill 后，同步更新本 README 的 Skills 列表。

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
