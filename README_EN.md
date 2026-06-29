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

## Recommended Skill Structure

```text
skill-name/
├── SKILL.md
├── README.md
├── examples/
├── assets/
└── scripts/
```

Where:

* `SKILL.md`: The main instruction file for the skill.
* `README.md`: Optional documentation for the specific skill.
* `examples/`: Optional examples of inputs, outputs, or use cases.
* `assets/`: Optional images, templates, references, or supporting materials.
* `scripts/`: Optional helper scripts.

## How to Add a New Skill

Create a new skill folder under the `skills/` directory:

```bash
mkdir skills/new-skill-name
touch skills/new-skill-name/SKILL.md
```

Then edit `SKILL.md` and describe the purpose, usage, input/output requirements, and important notes for the skill.

After adding the new skill, update the Skills table in this README and push the changes to GitHub:

```bash
git add .
git commit -m "Add new skill"
git push
```

## Maintenance Guidelines

To keep this repository easy to maintain, please follow these guidelines:

1. Each skill should have its own independent folder.
2. Each skill should include at least one `SKILL.md` file.
3. Folder names should use lowercase English words with hyphens, such as `document-analysis`.
4. Skills should remain as independent as possible.
5. Examples, assets, scripts, and supporting files should stay inside the corresponding skill folder.
6. Update the Skills table whenever a skill is added or modified.

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
