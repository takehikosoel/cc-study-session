# Claude Code 勉強会 台本（発表者用）

## 形式
- ハンズオン統合型（作業しながら概念を教える）
- 参加者はガイド（guide.md）を見ながら進行
- 発表者はこの台本で進行し、適宜デモやファイルを見せる

## 準備
- [ ] guide.md を参加者に共有済み
- [ ] ターミナル2つ準備（作業用 + デモ用）
- [ ] Claude Codeの起動テスト完了
- [ ] ~/Desktop/influencer-db/ が存在しないことを確認

---

## 導入: なぜ今Claude Codeを学ぶのか（0:00-0:10）10分

### 話すこと
- 「今日は講義を聞くだけじゃなく、実際にプロジェクトを1つ作ります」
- 「インフルエンサーデータベースを、Claude Codeを使ってゼロから構築します」
- 「作業の中で、概念を都度説明していきます」

**AIと人間の役割分担:**
- 「まず大前提。AIは『何を作るか』を決められない。それを決めるのは皆さんです」
- 「AIが得意なのは、要件からコード生成、大量ファイル一括編集、定型作業の自動化」
- 「人間が得意なのは、要件・判断、レビュー・承認、業務知識、運用方針」
- 「今日は『あなたが要件を出して、Claude Codeが設計・実装する』という役割分担を体験します」

**世界の事例を紹介:**
- 「経費精算を30分→5分にした事例。MoneyForward CSV解析→Gmail領収書検索→科目マッピング」
- 「PMがPRD作成をClaude Codeと壁打ちで行う事例。エンジニアでなくても参加できる」
- 「カンリー社の全エンジニア導入。個人の工夫をチーム資産にする」
- 「私たちの事例：BtoBマーケ自動化、Instagram月次報告書自動生成、Discord経由リモート操作」
- 「『これをやっていない組織との生産性の差がつきすぎて、変化に適応できない組織はあと数ヶ月もすると一瞬で社会から置いていかれる』」

**Claude Codeとは:**
- 「ChatGPTとの違い：ChatGPTは電話相談、Claude Codeは隣でPC操作してくれる同僚」
- 「大事なのは、Claude Codeは実際にファイルを操作するということ。だから安全設計が必要」
- 「覚えるコマンドは5つ。Esc、/clear、/context、/plan、Esc x2」

### デモ・見せるもの
- ガイドの「AIと人間、それぞれの得意なこと」の表を一緒に読む
- ガイドの「世界ではどう使われているか」セクションを一緒に読む

---

## Step 1: 作業場所を作って、Claude Codeを立ち上げよう（0:10-0:20）10分

### 話すこと
- 「まずフォルダを作ってClaude Codeを起動しましょう」
- 「全員一緒にやります。ターミナルを開いてください」
- 「ディレクトリとはフォルダのこと。ターミナルではフォルダのことをディレクトリと呼ぶ」

### 参加者と一緒に実行
```bash
mkdir ~/Desktop/influencer-db
cd ~/Desktop/influencer-db
git init
claude
```

**Finderとの対比を見せる:**

| コマンド | Finderで言うと |
|---------|-------------|
| `mkdir ~/Desktop/influencer-db` | 右クリック→新規フォルダ |
| `cd ~/Desktop/influencer-db` | フォルダをダブルクリックして開いた |
| `git init` | （Finderにはない機能。変更履歴の記録を開始） |

- 「Finderで実際にフォルダができているか確認してみてください」
- 「> が出たら成功です」
- 「『このフォルダの中身を教えて』と入力してみてください」
- 「空っぽですね。これからファイルを作っていきます」

### 確認ポイント
- 全員が claude を起動できているか
- > プロンプトが表示されているか

---

## Step 2: プロジェクトの説明書を作ろう（0:20-0:35）15分

### 話すこと
- 「最初に作るのはCLAUDE.md。これがClaude Codeへの『引き継ぎメモ』です」
- 「毎回セッション開始時にClaude Codeが読む。だから毎回説明しなくていい」
- 「ガイドに書いてある指示をそのままClaude Codeに入力してください」

### 参加者と一緒に実行
- ガイドの Step 2 の指示をClaude Codeに入力
- 許可画面が出る → 「yを押してください。これが安全設計です」
- 「許可画面でTabを押すと追加指示を入力できる。yかnだけじゃなく、微調整ができる」

### 作成後の解説（5分）
- 「今作ったCLAUDE.mdの中身を見てみましょう」
- 「Goal / Tech Stack / Directory / Rules の4セクション。これがお手本」
- **参考プロジェクトを見せる:**
```bash
cat /Users/satoutakehiko/Desktop/cc_folder/soel-btob-marketing/CLAUDE.md
```
- 「実際に運用中のプロジェクトも同じ構成。35行で収まっている」
- 「50行以内がルール。指示が多いと全体の遵守率が下がる」
- 「書くもの/書かないもの（ガイドの表を参照）」

### 参照ファイル
- /Users/satoutakehiko/Desktop/cc_folder/soel-btob-marketing/CLAUDE.md

---

## Step 3: 安全設定をしよう（0:35-0:50）15分

### 話すこと
- 「次はセキュリティ。ここが一番大事なパートです」
- 「Claude Codeはチャットと違って、実際にコマンドを実行する。だからガードレールが必要」

### 参加者と一緒に実行
- ガイドの Step 3 の指示をClaude Codeに入力
- settings.json と .gitignore が作成される

### 作成後の解説（10分）
**ここに時間をかける。以下の順番で解説:**

1. **.envファイルの仕組み**
   - 「.envは金庫。APIキーやパスワードを保管する専用ファイル」
   - 「コードに直接書くと、GitHubに上げた瞬間に世界中に公開される」
   - 「実際にAPIキー流出→高額請求の事故が多発している」
   - 「だから.envに書いて、コードには『環境変数から取れ』とだけ書く」

2. **なぜClaude Codeに.envを読ませないか**
   - 「読ませると会話履歴に秘密情報が残る」
   - 「だからsettings.jsonで物理的にブロックしている」

3. **各deny設定の理由**
   - 「rm -rf：一度実行すると元に戻せない」
   - 「git push --force：チームの作業が全部消える」
   - 「包丁は便利だが子供には持たせない」

4. **3層防御**
   - 「settings.json → rules/security.md → 許可ダイアログの3層」
   - 「1つが抜けても他で止まる設計」

**実際の設定を見せる:**
```bash
cat ~/.claude/settings.json
cat ~/.claude/rules/security.md
```

### 参照ファイル
- ~/.claude/settings.json
- ~/.claude/rules/security.md

---

## Step 4: どんなデータベースにするか設計しよう（0:50-1:05）15分

### 話すこと
- 「ここからPSBフレームワークのP（Plan）を実践します」
- 「Plan Modeに入ります。/plan と入力してください」
- 「Plan Mode = 読み取り専用。ファイルを変更しない安全モード」
- 「いきなり『作って』と頼むと間違った方向に走る。だから最初に計画を立てる」

### 参加者と一緒に実行
1. `/plan` で Plan Mode に入る
2. ガイドの Step 4 の指示を入力（要件書を丸ごと貼り付け）
3. 設計が出てくるのを待つ

### 設計が出た後の解説
- 「これがPSBフレームワーク。Plan → Setup → Build」
- 「Step 2-3 がSetup、今がPlan、次からBuild」
- 「各フェーズの間で/clearするのが鉄則」
- 「3つのモードのまとめ（ガイドの表を参照）」
- 「Plan Modeの承認画面が出たら、『Yes, clear context and auto-accept edits』を選ぶのが推奨。調査で溜まったコンテキストをクリアして計画だけ残して実行できる」

**実際の開発ルールを見せる:**
```bash
cat ~/.claude/rules/development.md
```

### 参照ファイル
- ~/.claude/rules/development.md

---

## Step 5: 記憶をリセットして実装に備えよう（1:05-1:10）5分

### 話すこと
- 「設計を確認したら、Plan Modeを解除して /clear します」
- 「ここでコンテキスト管理の話をします」
- 「コンテキスト＝Claude Codeの短期記憶。会話が長くなると精度が落ちる」
- 「95%を超えると自動圧縮されて指示を忘れることがある」
- 「だから作業の区切りごとに /clear する。これが一番大事」
- 「管理テクニック：/clear、/context、Document & Clear」

**Document & Clear を実演:**
- 「/clearする前に、必ず進捗を記録させる」
- 「『ここまでの進捗と決定事項を progress.md に書き出してください』と入力」
- 「書き出しが終わったら /clear」
- 「次のステップで '@progress.md を読んでから作業してください' と伝える」
- 「これがDocument & Clear。記憶をリセットしても、ファイルに書いてあるから引き継げる」

### 参加者と一緒に実行
1. 進捗を progress.md に書き出す指示を入力
2. `/clear` 実行

---

## Step 6: インフルエンサー図鑑を実装しよう（1:10-1:30）20分

### 話すこと
- 「PSBのB（Build）に入ります。まず /clear」
- 「実装の指示は具体的に。ファイル名と中身を指定する」
- 「『CLAUDE.mdを読んでから』と入れるのがポイント。引き継ぎメモを確認してから作業させる」

### 参加者と一緒に実行
1. `/clear`
2. ガイドの Step 6 の指示を入力
3. 実装が進むのを見守る（許可画面が出たら y）

### 作業中の補足
- 「許可画面の中身を見る習慣をつけてください」
- 「Always allowは便利だが乱用しない。慣れが一番危険」
- 「家の鍵を渡すのと、毎回インターホンで確認するのと。面倒でもインターホンが安全」

### API概念の解説（実装中の待ち時間に）
- 「実装の中で『API』という言葉が出てくるので整理します」
- 「API＝あるサービスの機能を外部から利用するための窓口。レストランの注文カウンター」

**このプロジェクトで使うAPI:**

| API | 誰が提供 | 何ができる |
|-----|---------|----------|
| Instagram Graph API | Meta社 | フォロワー数、投稿データ、エンゲージメント率の取得 |
| Claude API | Anthropic社 | AIにテキスト生成・分析をさせる |
| Google Sheets API | Google | スプレッドシートの読み書き |

- 「APIキー＝レストランの会員カード。利用許可の証明。だからStep 3で.envに保管した」
- 「LLM API：Claude Code自体も裏でLLM APIを使っている。話しかけるたびにAnthropic社のAPIにリクエストが送られる」

**API vs MCP:**

| | API | MCP |
|--|-----|-----|
| 何が起きる | コードが生成される | Claude Codeが外部サービスに直接アクセス |
| Claude Code閉じたら？ | コードが残るから動き続ける | 終わり |
| 例えるなら | レシピを書いてもらう→次から自分で作れる | 専属シェフを雇う→帰ったら作れない |

- 「今回のプロジェクトではAPI方式を使う。コードとして残るので、一度作ればClaude Codeなしでも動く」

### デモ・見せるもの
- ガイドの「良い指示の出し方」3つのポイントを強調

---

## Step 7: ちゃんとできたか確認しよう（1:30-1:35）5分

### 話すこと
- 「最後に検証。公式が最も強調しているポイント」
- 「『作って』で終わりにせず、『確認して』まで指示する」
- 「/clear してから検証フェーズへ」

### 参加者と一緒に実行
1. `/clear`
2. ガイドの Step 7 の指示を入力
3. 検証結果を確認

---

## Step 8: Gitでコミットしよう（1:35-1:45）10分

### 話すこと
- 「ここまでの作業をGitに記録します」
- 「Claude Codeに『コミットして』と言うだけ。Gitコマンドを覚える必要はない」

### 参加者と一緒に実行
- ガイドの Step 8 の指示を入力
- Claude Code が git add と git commit を実行

### Gitの便利さを補足

| やりたいこと | Claude Codeへの指示 |
|------------|-------------------|
| 変更を記録する | 「コミットして」 |
| 変更履歴を見る | 「最近のコミット履歴を見せて」 |
| ブランチを作る | 「新しいブランチを作って」 |
| 前の状態に戻す | 「直前のコミットに戻して」 |

### GitHub・SSH認証・gh CLIの紹介
- 「チームで共有するにはGitHubが必要。ここでは概要だけ紹介します」

**1. GitHubアカウント作成**
- 「https://github.com でSign up」

**2. SSH鍵の作成と登録**
- 「パスワードの代わりに鍵を使う仕組み」
- 「Claude Codeに『SSHキーを作成してGitHubに登録する手順を教えて』と聞ける」
- SSH鍵作成→GitHubのSettings→SSH and GPG keys→New SSH keyで登録

**3. 接続テスト**
```bash
ssh -T git@github.com
```

**4. GitHub CLI（gh）のインストール**
```bash
brew install gh
gh auth login
```
- 「ghがあると、Claude Codeからリポジトリ作成・PR作成まで全部自然言語でできる」

**5. GitHubにプッシュ**
- 「『GitHubにリポジトリを作成してプッシュして。プライベートリポジトリで』と言うだけ」

---

## Step 9: サーバーを起動してみよう（1:45-1:55）10分

### 話すこと
- 「/clear してから、サーバーを作ってもらいます」
- 「ガイドの Step 9 の指示を入力」

### 参加者と一緒に実行
1. `/clear`
2. ガイドの Step 9 の指示を入力
3. Claude Codeが必要なファイルを作成
4. サーバーを起動してブラウザで確認

```bash
pip install -r requirements.txt
python app.py
```

- 「ブラウザで http://localhost:5000 を開くと、インフルエンサー一覧が表示される」
- 「ここで拍手。非エンジニアが、要件書からWebアプリを立ち上げるところまで2時間でできました」

---

## Step 10: 使い方を分析して、ショートカットを作ろう（1:55-2:10）15分

### 話すこと
- 「ここまでたくさんClaude Codeを使ってきました。ここで /insights を実行してみてください」

### /insights の実演
- `/insights` を実行
- 「過去のセッションを分析して改善提案を自動生成する機能」

| 提案の種類 | 何をしてくれる |
|-----------|-------------|
| CLAUDE.mdへの追加ルール | 具体的な文章で追加を提案 |
| Skills（ショートカット）の提案 | 繰り返し操作パターンを検出してSkill化を提案 |
| Hooksの提案 | 過去の問題を防ぐ自動チェックを提案 |
| MCPサーバーの提案 | 作業内容に応じたツール連携を推奨 |

### /insights の提案に従ってSkillsを作成
- 「提案に従ってショートカットを作りましょう」
- 「いきなりSkillを作らない。まず実際にタスクを成功させて、うまくいったアプローチをSkillに抽出する。これが正しい順序」

### Skillsの3層構造を解説

| 層 | 何を置く | いつ読み込まれる |
|---|---------|-------------|
| 第1層：YAMLフロントマター | 「いつ使うか」の最小情報 | 常時（毎セッション） |
| 第2層：SKILL.md本文 | 本体の指示 | Skillが発動したとき |
| 第3層：references/ | 詳細ドキュメント | 必要時のみ |

### descriptionの書き方
- 「Skillが自動で発動するかどうかは description で決まる」
- 「何をするか / いつ使うか / 主要な機能 の3要素を含める」

```yaml
# 良い例
description: インフルエンサーをジャンル・フォロワー数で検索する。
  「インフルエンサー検索」「候補を探して」と言われたときに使用。

# 悪い例
description: データを検索します。
```

### Skills vs Hooks vs Rules vs Loop の比較

| 仕組み | いつ動く | 何をする | 例え |
|-------|---------|---------|------|
| **Skills** | `/コマンド名` で呼ぶ or 自動検出 | よく使う指示セットを実行 | レシピ本 |
| **Hooks** | ツール実行の前後に自動発動 | 安全チェック・自動フォーマット | 火災報知器 |
| **Rules** | セッション開始時に自動読み込み | Claude Codeの判断基準を設定 | 社内ルールブック |
| **Loop** | 定期間隔で繰り返し実行 | 定期チェック・監視タスク | 定時パトロール |

**使い分け:**
- 毎回同じ操作をしている → Skills
- 操作の前後で必ずチェックしたい → Hooks
- Claude Codeの振る舞いを全体的に変えたい → Rules
- 定期的に繰り返したい → Loop

**参考プロジェクトのSkillsを見せる:**
```bash
ls /Users/satoutakehiko/Desktop/cc_folder/soel-btob-marketing/.claude/skills/
```
- 「このプロジェクトには9個のSkillsがある。/insightsの提案に従って増やしていった結果」

### 参照ファイル
- /Users/satoutakehiko/Desktop/cc_folder/soel-btob-marketing/.claude/skills/
- ~/.claude/skills/

---

## Step 11: 完成！振り返ろう（2:10-2:15）5分

### 話すこと
- 「完成したフォルダ構成を見てみましょう」
- 「今日やったことの全体像」

```
1. ディレクトリ作成 → Claude Code起動
2. CLAUDE.md（説明書）作成
3. 安全設定（settings.json + .gitignore）
4. Plan Modeで要件定義 → 設計
5. /clear（記録してからリセット = Document & Clear）
6. 実装（データモデル + サンプルデータ + API概念）
7. 検証
8. Gitコミット（+ GitHub/SSH/gh CLI紹介）
9. サーバー起動 → ブラウザで確認
10. /insights で分析 → Skills作成
```

- 「要件書 → 設計 → 実装 → 動作確認 → Git記録 → 改善 の一連の開発フローを体験しました」

**失敗パターン TOP 3:**
- キッチンシンク → 今日は各Stepで/clearした
- 修正ループ → 2回失敗したら/clear→より良い指示
- CLAUDE.md肥大化 → 50行以内で作った

**明日から実践する3つ:**
1. `/clear` を習慣にする
2. まず `/plan` で設計してから作る
3. `@ファイル名` で手元の資料を読み込ませる

---

## Step 12: ここから先の世界（2:15-2:20）5分

### 話すこと

**グローバル設定を見せる:**
```bash
ls ~/.claude/
ls ~/.claude/rules/
ls ~/.claude/skills/
```
- 「グローバル（全プロジェクト共通）とプロジェクト固有の2層構造」
- 「安全ルールや開発フレームワークは全プロジェクト共通にしておく」
- 「CLAUDE.mdが大きくなったら .claude/rules/ にトピックごとに分割できる」

**リモートコントロール事例を紹介:**
```bash
cat /Users/satoutakehiko/Desktop/cc-ops-planning/CLAUDE.md
```
- 「Discord経由でスマホからClaude Codeを操作する仕組み」
- 「毎朝6:00に『今日やるべきこと』がDiscordに届く」
- 「スマホから『あれやっとけ』→ Claude Codeが実行 → 結果がDiscordに返る」
- 「これが今日学んだSkills・Hooks・API/MCPを組み合わせた先にある世界」

### 参照ファイル
- /Users/satoutakehiko/Desktop/cc-ops-planning/CLAUDE.md

---

## 全体で参照するファイル一覧

### グローバル設定
| ファイル | パス | タイミング |
|---------|------|----------|
| settings.json | ~/.claude/settings.json | Step 3 |
| development.md | ~/.claude/rules/development.md | Step 4 |
| security.md | ~/.claude/rules/security.md | Step 3 |
| グローバルskills | ~/.claude/skills/ | Step 10, 12 |

### 参考プロジェクト
| ファイル | パス | タイミング |
|---------|------|----------|
| CLAUDE.md | /Users/satoutakehiko/Desktop/cc_folder/soel-btob-marketing/CLAUDE.md | Step 2 |
| Skills | /Users/satoutakehiko/Desktop/cc_folder/soel-btob-marketing/.claude/skills/ | Step 10 |
| Ops設計書 | /Users/satoutakehiko/Desktop/cc-ops-planning/CLAUDE.md | Step 12 |

### 今日作るプロジェクト
| ファイル | パス | タイミング |
|---------|------|----------|
| 作業ディレクトリ | ~/Desktop/influencer-db/ | Step 1 で作成 |
