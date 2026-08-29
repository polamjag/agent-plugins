# personal-agent-skills

Claude Code と Codex で共用する、自作 Agent Skills の保存リポジトリ。

## 構成

```text
skills/<skill-name>/       スキル本体（唯一の編集元）
.claude/skills/            Claude Code 用リンク
.agents/skills/            Codex 用リンク
scripts/new-skill          スキルの雛形作成とリンク生成
scripts/link-skills        既存スキルのリンク再生成
scripts/validate-skills    全スキルの簡易検証
```

各スキルは `SKILL.md` を必須とし、必要に応じて `scripts/`、`references/`、`assets/`、`agents/openai.yaml` を追加する。

## 新しいスキル

```sh
./scripts/new-skill my-skill
```

生成後、`skills/my-skill/SKILL.md` の説明と本文を編集する。Claude Code と Codex の探索先には同じスキルへの相対リンクが作成される。

既存 clone で探索用リンクを再生成する場合:

```sh
./scripts/link-skills
```

## 検証

```sh
./scripts/validate-skills
```

検証対象はディレクトリ名、`SKILL.md` の存在、YAML frontmatter、必須の `name` と `description`、探索用リンク。

## 運用方針

- スキル名は小文字英数字とハイフンのみ、64 文字未満
- 汎用的な指示は短く保ち、詳細資料は `references/` に分離
- 決定的な処理が必要な場合だけ `scripts/` を追加
- 製品固有の frontmatter は原則避け、Claude Code と Codex の共通形式を優先
- 秘密情報、認証情報、端末固有の絶対パスはコミットしない

## 利用

このリポジトリ直下、またはその配下で各エージェントを起動する。新しいトップレベルの skills ディレクトリが実行中に追加された場合は、エージェントを再起動する。
