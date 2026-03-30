# Claude Code 勉強会資料

社内向けClaude Code勉強会の資料一式です。

## 構成

```
├── guide.md                          # 参加者配布用ガイド（メイン資料）
├── script.md                         # 発表者用台本
├── slides.html                       # スライド（ブラウザで開く）
└── reference/                        # 社内ナレッジ
    ├── CC開発チートシート.md            # Claude Code開発の要点まとめ
    ├── settings-example.json          # settings.json のサンプル（denyリスト）
    ├── rules/
    │   ├── development.md             # 開発ルール（PSBフレームワーク）
    │   └── security.md                # セキュリティルール
    └── skills/
        ├── api-check/SKILL.md         # API連携時のドキュメント確認
        ├── audit-existing/SKILL.md    # 実装前の既存コード確認
        ├── plan-first/SKILL.md        # 計画先行の強制
        └── verify-before-done/SKILL.md # 完了前の動作確認
```

## 勉強会の進め方

- **形式:** ハンズオン中心（約2時間）
- **対象:** 非エンジニア（Claude Codeセットアップ済み）
- **内容:** インフルエンサーデータベースをゼロから構築しながら、Claude Codeの概念を学ぶ

### ステップ

1. 作業場所を作ってClaude Codeを起動
2. CLAUDE.md（プロジェクト説明書）を作成
3. 安全設定（settings.json + .gitignore）
4. Plan Modeで要件定義・設計
5. /clear でリセット（Document & Clear）
6. 実装（データモデル + サンプルデータ）
7. 検証
8. Gitコミット + GitHub連携
9. サーバー起動
10. /insights で分析 → Skills作成
11. 振り返り
12. 応用（グローバル設定・リモートコントロール）

## reference/ の使い方

### 自分のClaude Codeに適用する

```bash
# ルールをコピー
cp reference/rules/development.md ~/.claude/rules/
cp reference/rules/security.md ~/.claude/rules/

# スキルをコピー
cp -r reference/skills/* ~/.claude/skills/

# settings.json は中身を確認してから手動でマージ
cat reference/settings-example.json
```

### CC開発チートシート

`reference/CC開発チートシート.md` に開発の要点がまとまっています。
PSBフレームワーク、コンテキスト管理、CLAUDE.mdの書き方、サブエージェントの使い方など。

## 参照元

- [公式ベストプラクティス](https://code.claude.com/docs/ja/best-practices)
- [17 Best Claude Code Workflows](https://medium.com/@joe.njenga/17-best-claude-code-workflows-that-separate-amateurs-from-pros-instantly-level-up-5075680d4c49)
- [カンリー社内Claude Code勉強会資料](https://zenn.dev/canly/articles/cc0891517e45cc)
- [Claude Codeですべての日常業務を爆速化しよう！](https://qiita.com/minorun365/items/114f53def8cb0db60f47)
- [Claude Code Insights](https://zenn.dev/ischca/articles/cc-guide-insights)
