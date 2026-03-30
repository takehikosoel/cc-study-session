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

## 参照元リンク集

### 公式ドキュメント
- [Claude Code ベストプラクティス（公式・日本語）](https://code.claude.com/docs/ja/best-practices)
- [Claude Code CHANGELOG](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)

### ベストプラクティス・ワークフロー
- [17 Best Claude Code Workflows That Separate Amateurs from Pros](https://medium.com/@joe.njenga/17-best-claude-code-workflows-that-separate-amateurs-from-pros-instantly-level-up-5075680d4c49) -- Joe Njenga
- [The Shorthand Guide to Everything Claude Code](https://x.com/affaanmustafa/status/2012378465664745795) -- @affaanmustafa
- [The Complete Claude Code Tutorial](https://x.com/eyad_khrais/status/2010076957938188661) -- @eyad_khrais
- [Claude needs 4 things at all times](https://x.com/BharukaShraddha/status/2029836408232497678) -- @BharukaShraddha
- [とてつもなくシンプルなClaude Code開発者によるCCの使い方](https://x.com/shinojapan/status/2007254196077375970) -- @shinojapan

### 非エンジニア向け・業務活用
- [Claude Codeですべての日常業務を爆速化しよう！](https://qiita.com/minorun365/items/114f53def8cb0db60f47) -- minorun365
- [Claude Codeで異次元の仕事をする方法（非エンジニアにも全力推奨）](https://note.com/sunazuka/n/n258295d054ca) -- 砂塚紀彦
- [PM向けClaude Codeコース](https://github.com/carlvellotti/claude-code-pm-course) -- carlvellotti
- [Claude Code 超完全ガイド（エンジニアから投資家まで）](https://note.com/fabymetal/n/n3f0f2873b56c) -- FabyΔ
- [Claude Codeとは？導入・使い方・安全運用ガイド](https://ensou.app/blog/claude-code-business-guide/) -- AIエージェント活用ノウハウ

### セキュリティ
- [Claude Codeを使うなら、この「7つのセキュリティ設定」は最低限見ておいて欲しい](https://x.com/SuguruKun_ai/status/2035657076371075514) -- @SuguruKun_ai

### 拡張機能・Skills・Hooks
- [Claude Code Insights](https://zenn.dev/ischca/articles/cc-guide-insights) -- ischca
- [Claude CodeのHooksをハックして自律駆動するマルチエージェントを作った](https://zenn.dev/zaico/articles/d6b882c78fe4b3) -- zaico
- [8年のプロダクトデザイン経験をClaude Skillに凝縮した](https://www.reddit.com/r/ClaudeAI/comments/1q4l76k/i_condensed_8_years_of_product_design_experience/) -- Reddit
- [承認疲れをAIで解決 (ccmanager)](https://github.com/kbwo/ccmanager) -- kbwo

### Agent Teams・並列開発
- [Agent Teamを導入したら圧倒的に質が変わった](https://x.com/shinojapan/status/2019620314867724681) -- @shinojapan
- [ClaudeCodeのAgent Teamsを体験できる手順書](https://note.com/suh_sunaneko/n/nfe794eac6a23) -- すぅ

### Discord連携
- [Claude Code Discord Bridge](https://github.com/ebibibi/claude-code-discord-bridge) -- ebibibi

### キャリア・戦略
- [Claude Code時代のソフトウェアエンジニア生存戦略](https://note.com/suthio/n/n4f79fbe4efda) -- suthio
