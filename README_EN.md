# AlwaysUseful Skills

[中文](./README.md) | **English**

AlwaysUseful Skills is a repository for organizing, maintaining, and reusing AI skills.

This repository uses a unified `skills/` directory to manage multiple independent skills. Each skill should be placed in its own subfolder and should include at least one `SKILL.md` file. Additional files such as README files, examples, scripts, assets, or supporting documents can be added when needed.

## Repository Structure

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

## Skills

| Skill Name     | Description                                                                       | Path                   |
| -------------- | --------------------------------------------------------------------------------- | ---------------------- |
| `mdoc-present` | Convert any Markdown document into a self-contained canonical HTML presentation.  | `skills/mdoc-present/` |

> When adding new skills, update this table with the corresponding name, description, and path.

## Security Notes

Do not commit the following content:

* API keys
* Tokens
* Passwords
* `.env` files
* Private configuration files
* Personal information
* Unsanitized business data

If configuration examples are needed, use `.env.example` and make sure it does not contain real secrets.

## License

This repository has not specified a license yet.
