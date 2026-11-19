---
layout: default
title: "GitHubトレンドリポジトリ レビュー(週間: 2026年11月19日時点)"
---

# GitHubトレンド週間レビュー（2026年11月19日時点）

## 全体トレンドの概観

Web制作の指針、画面部品、ブラウザでの確認を組み合わせるプロジェクトが目立つ。Modern Web GuidanceはAIに新しいWeb標準の使い方を教え、AstryxはReactの画面部品を提供する。Stitch Skillsはデザインから実装への作業を支援し、Chrome DevTools MCPとagent-browserは実際の画面を操作して結果を確かめる。作り方の指示から、表示や操作の確認までをつなぐ顔ぶれになった。

コードの品質確認も厚い。Open Code Reviewは変更差分のレビュー、Claude-BugHunterは許可された対象での脆弱性調査、Codex Securityはコードの調査から修正・検証までを扱う。Plannotatorは、AIが作った計画やHTML、差分に人が注釈を返すためのもの。自動処理を増やしながら、指摘の根拠と人の確認を残す構成に注目したい。

家計・資産管理のSure、投資判断の手順を整理するClaude Trading Skills、銘柄別の調査報告を自動化するdaily_stock_analysisも含まれる。これらは目的が異なり、同じ投資AIとして扱うと用途を見誤る。AG-UIの画面連携やUniverの編集機能も含め、生成した文章をアプリ上の作業へ結び付ける試みが多い。

## リポジトリ別サマリー

### 1. GoogleChrome/modern-web-guidance-src

- **リンク**：[https://github.com/GoogleChrome/modern-web-guidance-src](https://github.com/GoogleChrome/modern-web-guidance-src)
- **概要・目的**：AI開発ツールへWeb標準の使い方、実装上の注意、ブラウザ互換性の情報を渡すModern Web Guidanceの原本・評価用リポジトリ。
- **主な特徴**：CSSレイアウト、フォーム、アクセシビリティ、性能などの指針を検索して必要な分だけ参照する。古い実装パターンの検出や評価の仕組みを備える。コードはApache-2.0、ガイド文書はCC BY 4.0。配布用リポジトリと、この原本側は役割が異なる。[README](https://github.com/GoogleChrome/modern-web-guidance-src#readme)
- **想定用途・対象者**：AIが生成したWeb画面を改善する開発者。HTML資料の画面幅への対応や、不要なJavaScriptを減らす検討にも使える。
- **その他特筆事項**：新しいAPIは対象ブラウザの対応状況と代替手段を確認して採用する。指針の評価結果は、個別アプリの品質保証にはならない。総スター8,824（今週+7,015）。
- **トレンド入りの理由**：agent-browserは11月13日（日本時間）のv0.43.0で、この指針を取得して実画面を確認するスキルを追加した。実装の助言を動作確認へつなぐ具体的な採用例があり、関心の背景として考えられる。スター増加との直接の因果は未確認。[公式文書](https://developer.chrome.com/docs/modern-web-guidance)、[採用先のリリース](https://github.com/vercel-labs/agent-browser/releases/tag/v0.43.0)

### 2. backnotprop/plannotator

- **リンク**：[https://github.com/backnotprop/plannotator](https://github.com/backnotprop/plannotator)
- **概要・目的**：AIが提示した計画、仕様書、HTML、コード差分を人が確認し、注釈やコメントをAIへ返すためのローカルなレビュー画面。
- **主な特徴**：複数AIからの質問や成果物をまとめるInbox、文書への注釈、ローカル差分とPRのレビューに対応する。プラグイン、フック、MCPなどでAI開発ツールと接続する。Apache-2.0またはMITを選択できる。[README](https://github.com/backnotprop/plannotator#readme)
- **想定用途・対象者**：生成した画面の修正箇所を具体的に伝えたい開発者やレビュアー。複数のAIへ仕事を依頼し、確認待ちの成果物を整理したい場合にも向く。
- **その他特筆事項**：コメントの送信と修正の完了は別に確認する。ローカル画面の利用でも、接続するAIやリモート機能への送信範囲は構成によって変わる。総スター13,445（今週+2,926）。
- **トレンド入りの理由**：11月12日のv0.28.62で、InboxからのWindows上のエージェント起動を修正し、モデルや推論量の選択、独自ルールの設定を追加した。Windowsでもレビューと依頼をまとめやすくする整備は注目背景と考えられる。掲載の直接要因は未確認。[公式リリース](https://github.com/backnotprop/plannotator/releases/tag/v0.28.62)

### 3. elementalsouls/Claude-BugHunter

- **リンク**：[https://github.com/elementalsouls/Claude-BugHunter](https://github.com/elementalsouls/Claude-BugHunter)
- **概要・目的**：許可された対象のバグバウンティ調査やレッドチーム業務をClaude Codeで支援する、調査手順と参考資料のスキル集。
- **主な特徴**：Webアプリや企業の認証・基盤に関する調査分類、公開報告を基にしたパターン、候補の検証、証拠整理、報告を収録する。Burp MCP連携や案件フォルダの作成も扱う。コードはMIT、手法・辞書・文書などの内容はCC BY 4.0。[README](https://github.com/elementalsouls/Claude-BugHunter#readme)
- **想定用途・対象者**：調査範囲と実施許可が明確な脆弱性診断の担当者。調査漏れの確認や、再現証拠をそろえる手順の参照に使う。
- **その他特筆事項**：資料の件数や作者の実績説明は、診断の網羅性や検出精度の保証ではない。公開版のリリースノートと現在のREADMEでは収録数が異なるため、導入版を固定して確認したい。総スター11,332（今週+2,508）。
- **トレンド入りの理由**：公式リリースでは、調査分類の拡充に加えてスキルの品質・安全性を確認するCIを整えた経緯を確認できる。探索だけでなく検証と報告までまとめて参照できる点は背景として考えられる。ただし確認できたv2.1の公開は6月で、今週の新発表ではない。今週固有の拡散要因は未確認。[公式リリース](https://github.com/elementalsouls/Claude-BugHunter/releases/tag/v2.1)

### 4. meta/astryx

- **リンク**：[https://github.com/meta/astryx](https://github.com/meta/astryx)
- **概要・目的**：人とAI開発ツールが共通の部品・規約を使って画面を作るための、Meta由来のReactデザインシステム。
- **主な特徴**：React 19以降向けの画面部品、テーマ、ダークモード、テンプレート、CLIを提供する。内部ではStyleXを利用し、利用側はCSSのクラスや変数で見た目を調整できる。MIT。[README](https://github.com/meta/astryx#readme)
- **想定用途・対象者**：管理画面やWebアプリの部品をそろえたい開発者、デザイナー。AIが画面ごとに異なる実装を作る問題を減らす検討に向く。
- **その他特筆事項**：現在はベータ。Reactの要件と既存のデザイン規約との整合を確認する。アクセシブルな部品を使っても、画面全体の読み順やキーボード操作の確認は残る。総スター30,561（今週+8,700）。
- **トレンド入りの理由**：Metaの公式ブログは7月の公開後報告で、社内で育てた設計を、人とAIの双方が使える部品・文書・CLIとして公開した経緯を説明している。AIと共通の規約で実装できる点は注目背景と考えられる。今回の掲載を新規公開と同一視せず、今週の直接要因は未確認とする。[公式ブログ](https://astryx.atmeta.com/blog/one-month-of-astryx)

### 5. we-promise/sure

- **リンク**：[https://github.com/we-promise/sure](https://github.com/we-promise/sure)
- **概要・目的**：家計や資産の情報を管理する、自己ホスト可能な個人向け金融アプリ。開発が終了したMaybe Financeをコミュニティが引き継いだフォーク。
- **主な特徴**：Dockerでの自己ホスト、ブラウザや各種クライアントからの利用、取引・保有資産の取り込みや集計を扱う。Ruby、PostgreSQL、Redisを用いる。AGPLv3で、Maybeの商標と元プロジェクトとの関係にも注意書きがある。[README](https://github.com/we-promise/sure#readme)
- **想定用途・対象者**：自分で運用環境を管理し、家計・口座・資産の情報をまとめたい利用者。金融データを扱うアプリの設計を学ぶ開発者にも参考になる。
- **その他特筆事項**：口座連携の対応地域、データ提供元、バックアップと復元を確認する。日付付きのアルファ配布と安定版を区別し、実データの移行前に取り込み結果を照合したい。総スター16,490（今週+4,786）。
- **トレンド入りの理由**：11月17日のアルファ版では、IBKRの税・利息・手数料の取り込み、為替がない場合の処理、バックアップからの復元などを改善した。家計アプリとして使い続けるための整備は関心の背景と考えられる。更新と掲載の因果は未確認。[公式リリース](https://github.com/we-promise/sure/releases/tag/v2026.11.17-alpha)

### 6. alibaba/open-code-review

- **リンク**：[https://github.com/alibaba/open-code-review](https://github.com/alibaba/open-code-review)
- **概要・目的**：Gitの変更差分や指定したファイルをAIで調査し、該当行に対応するレビューコメントを作るCLI。
- **主な特徴**：対象ファイルの選択、関連ファイルのまとめ方、ルールの適用、コメント位置の補正を処理側で管理し、AIが周辺コードを調べる構成。設定したモデルでの実行と、接続元AIへ処理を委ねるモードがある。Apache-2.0。[README](https://github.com/alibaba/open-code-review#readme)
- **想定用途・対象者**：PRレビューの一次確認、未把握のコードの調査、CIへのレビュー組み込みを検討する開発者とチーム。
- **その他特筆事項**：Git 2.41以降が必要。作者の評価では誤検知の少なさを優先し、見逃しとの兼ね合いを説明している。評価値を自社コードの精度に置き換えず、既知の不具合を含む差分で確認したい。総スター54,167（今週+3,675）。
- **トレンド入りの理由**：公式READMEは、レビュー範囲の抜けやコメント位置のずれに対し、固定的な処理とAIの調査を組み合わせる方針を説明する。リリースでも、部分失敗を問題なしと表示しない修正を確認できる。レビュー結果の扱いやすさと失敗の可視化は注目背景と考えられるが、今週の直接要因は未確認。[公式リリース](https://github.com/alibaba/open-code-review/releases)

### 7. google-labs-code/stitch-skills

- **リンク**：[https://github.com/google-labs-code/stitch-skills](https://github.com/google-labs-code/stitch-skills)
- **概要・目的**：Google StitchをAI開発ツールから使い、画面のデザイン、既存コードの取り込み、実装への変換を進めるスキルとプラグインの集まり。
- **主な特徴**：画面生成・編集、DESIGN.mdの抽出、静的HTML化、Reactなどへの変換、複数ページの制作手順を収録する。Stitch MCPとの接続を前提とする。Apache-2.0。[README](https://github.com/google-labs-code/stitch-skills#readme)、[ライセンス](https://github.com/google-labs-code/stitch-skills/blob/main/LICENSE)
- **想定用途・対象者**：画面案と実装の間で見た目や部品の規約を引き継ぎたい開発者。既存の画面からデザイン方針を整理する用途にも向く。
- **その他特筆事項**：一部のスキルには依存関係があり、選択導入時は必要なものをそろえる。Stitchへのアップロードを含むため、送信するソースや素材の範囲を確認する。Googleの正式サポート製品ではない旨も明記。総スター10,388（今週+1,197）。
- **トレンド入りの理由**：公式READMEでは、デザイン、実装、補助処理をプラグインに分け、Codexなど複数の開発環境で使う経路を具体化している。画面案を作るだけでなく既存コードとの往復を扱う点は注目背景と考えられる。今週固有の発表・拡散要因は確認できなかった。[公式の機能・導入説明](https://github.com/google-labs-code/stitch-skills#available-plugins)

### 8. tradermonty/claude-trading-skills

- **リンク**：[https://github.com/tradermonty/claude-trading-skills](https://github.com/tradermonty/claude-trading-skills)
- **概要・目的**：個人投資家の市場確認、リスク管理、取引計画、記録と振り返りを整理するスキル集。
- **主な特徴**：日次の確認、長期保有の週次レビュー、取引後の振り返りなどを、使用スキル・判断条件・成果物の順序を示すワークフローにまとめる。外部APIが不要な入口と、データサービスを使う経路を分けている。MIT。[README](https://github.com/tradermonty/claude-trading-skills#readme)、[ライセンス](https://github.com/tradermonty/claude-trading-skills/blob/main/LICENSE)
- **想定用途・対象者**：調査や振り返りの手順をそろえたい個人投資家、金融情報の調査工程を学ぶ開発者。
- **その他特筆事項**：作者は教育・調査・手順改善向けと説明し、収益の保証や売買判断の委任を目的としていない。データの遅延、APIの条件、計算結果は別に検証する。総スター7,074（今週+2,985）。
- **トレンド入りの理由**：公式READMEは、スキルの一覧に加えて、目的別の入口、必要なAPI、判断を止める条件、記録する成果物を示す。多くの分析手法を実際の作業順にまとめた点は関心の背景と考えられる。今週固有の直接要因は未確認で、変更履歴のUnreleased項目を公開済みの更新とは扱わない。[公式ワークフロー説明](https://github.com/tradermonty/claude-trading-skills#recommended-starting-path)、[変更履歴](https://github.com/tradermonty/claude-trading-skills/blob/main/CHANGELOG.md)

### 9. ChromeDevTools/chrome-devtools-mcp

- **リンク**：[https://github.com/ChromeDevTools/chrome-devtools-mcp](https://github.com/ChromeDevTools/chrome-devtools-mcp)
- **概要・目的**：AIからChromeを操作し、画面、通信、コンソール、性能の問題を調べるためのMCPサーバーとCLI。
- **主な特徴**：性能トレースの記録と分析、通信内容の調査、スクリーンショット、操作結果を待つブラウザ自動化を提供する。Chrome DevToolsとPuppeteerを利用する。Apache-2.0。[README](https://github.com/ChromeDevTools/chrome-devtools-mcp#readme)、[ライセンス](https://github.com/ChromeDevTools/chrome-devtools-mcp/blob/main/LICENSE)
- **想定用途・対象者**：WebアプリやHTML資料の表示不具合、遅さ、操作失敗の原因を調べる開発者とテスト担当者。
- **その他特筆事項**：接続先ブラウザの内容をAIへ公開する。利用統計の送信は標準で有効で、停止オプションがある。性能分析ではCrUXへのURL送信も別設定のため、対象画面と送信設定を確認する。総スター58,206（今週+2,948）。
- **トレンド入りの理由**：11月11日の1.13.0で、ログポイントとページ単位の通信モックを追加した。問題が起きる条件を作り、実行中の状態を観察する機能は、AIによる不具合再現やテストの用途を広げる。注目背景として考えられるが、スター増加との直接の因果は未確認。[公式リリース](https://github.com/ChromeDevTools/chrome-devtools-mcp/releases/tag/chrome-devtools-mcp-v1.13.0)

### 10. anthropics/skills

- **リンク**：[https://github.com/anthropics/skills](https://github.com/anthropics/skills)
- **概要・目的**：AIへ専門作業の手順を教えるスキルの公式サンプル集。文書、スクリプト、参考資料をまとめ、必要なときに読み込ませる。
- **主な特徴**：文書作成、Webアプリのテスト、MCP開発、ブランドに合わせた制作などを扱う。SKILL.mdに用途と手順を記し、補助ファイルを組み合わせる。READMEは文書作成系を含めApache-2.0での公開を説明する。[README](https://github.com/anthropics/skills#readme)
- **想定用途・対象者**：資料作成や調査の繰り返し作業をそろえたい利用者、社内の確認条件をAI向け手順にする開発者。
- **その他特筆事項**：公開サンプルと製品内の実装・動作が同じとは限らない。自社の書式や入力で確認し、生成物を実際のアプリで検証する必要がある。総スター197,196（今週+4,847）。
- **トレンド入りの理由**：Anthropicは10月22日、Agent Skills仕様のAgentic AI Foundationへの寄贈を発表した。異なるAI環境で手順を共有する動きはサンプル集を参照する背景になる。仕様の寄贈と、この実装例の更新は区別し、今週の増加の直接原因は未確認とする。[公式発表](https://www.anthropic.com/news/donating-agent-skills-to-the-agentic-ai-foundation)

### 11. ZhuLinsen/daily_stock_analysis

- **リンク**：[https://github.com/ZhuLinsen/daily_stock_analysis](https://github.com/ZhuLinsen/daily_stock_analysis)
- **概要・目的**：登録した銘柄の価格、指標、ニュースなどを集め、AIで分析報告を作り、各種通知先へ定期配信するシステム。
- **主な特徴**：複数市場のデータ取得、Web・デスクトップ画面、履歴の閲覧、複数の分析手順、GitHub ActionsやDockerでの運用に対応する。市場ごとの対応範囲を別文書で説明する。MIT。[README](https://github.com/ZhuLinsen/daily_stock_analysis#readme)
- **想定用途・対象者**：銘柄調査の素材集めと報告作成を定期化したい利用者、データ取得からAI要約・通知までの構成を学ぶ開発者。
- **その他特筆事項**：作者は学習・研究目的とし、投資助言や損失の補償を提供していない。市場ごとの取引日、価格の調整方法、単位、ニュースの鮮度を確かめ、生成報告をそのまま判断根拠にしない。総スター73,339（今週+3,653）。
- **トレンド入りの理由**：11月16日のv3.35.0で台湾市場の分析対象を拡充し、取引日の比較基準、除息日の価格処理、金額・株数の単位なども修正した。対象市場を増やしつつ報告の前提を整える更新は関心の背景と考えられる。掲載との因果は未確認。[公式リリース](https://github.com/ZhuLinsen/daily_stock_analysis/releases/tag/v3.35.0)

### 12. mvanhorn/last30days-skill

- **リンク**：[https://github.com/mvanhorn/last30days-skill](https://github.com/mvanhorn/last30days-skill)
- **概要・目的**：あるテーマについて最近の投稿や活動を複数のサービスから集め、AIで調査メモにまとめるスキル。
- **主な特徴**：Reddit、Hacker News、GitHubなどを横断し、対応する認証・API設定により利用できる情報源を増やす。反応数などを用いて候補を整理し、任意で調査結果をローカル保存する。MIT。[README](https://github.com/mvanhorn/last30days-skill#readme)、[ライセンス](https://github.com/mvanhorn/last30days-skill/blob/main/LICENSE)
- **想定用途・対象者**：技術の反応、製品や企業の最近の活動、次に確認する話題を調べたい調査担当者。勉強会の話題探しにも使える。
- **その他特筆事項**：反応数や予測市場の情報は事実の正しさを保証しない。要約から原文へ戻り、投稿日と出来事の日付、情報源の偏りを確認する。APIやブラウザ認証によって取得できる範囲も変わる。総スター69,969（今週+1,548）。
- **トレンド入りの理由**：現行READMEはv4の横断調査の流れと設定方法を示し、11月18日（日本時間）のv4.3.1でも説明と導入まわりを更新した。複数の情報源を一つの調査メモにまとめる使い方は注目背景と考えられる。ただし、導入修正を今週の増加原因とは断定できない。[公式リリース](https://github.com/mvanhorn/last30days-skill/releases/tag/v4.3.1)

### 13. ag-ui-protocol/ag-ui

- **リンク**：[https://github.com/ag-ui-protocol/ag-ui](https://github.com/ag-ui-protocol/ag-ui)
- **概要・目的**：AIエージェントの処理経過、メッセージ、ツール実行、共有状態を、アプリの画面へ伝えるためのイベント型プロトコル。
- **主な特徴**：双方向のイベントストリームで、逐次表示、処理の中断・再開、人への確認、子エージェントの状態などを扱う。1.0では仕様とJSON Schemaを定め、TypeScript、Python、.NETのSDKを提供する。MIT。[README](https://github.com/ag-ui-protocol/ag-ui#readme)
- **想定用途・対象者**：AIの進捗や確認待ちを画面に表示するアプリの開発者。異なるエージェント基盤とWeb・モバイル画面を接続したい場合に向く。
- **その他特筆事項**：イベント形式の共通化だけで、アプリの認証、接続の復旧、処理の重複防止が完成するわけではない。停止と完了をどう表示するかも実装側で確認する。総スター20,419（今週+2,773）。
- **トレンド入りの理由**：公式1.0仕様は、実行終了時の成功・中断・キャンセル、子エージェントの帰属など、画面が処理状態を判断するための規則を明文化した。連携先ごとの独自処理を減らす基盤として注目できる。1.0の公表を今週の新発表とは扱わず、今週の直接要因は未確認。[公式変更点](https://docs.ag-ui.com/spec/1.0/changelog)

### 14. vercel-labs/agent-browser

- **リンク**：[https://github.com/vercel-labs/agent-browser](https://github.com/vercel-labs/agent-browser)
- **概要・目的**：AIがWebページを読み、入力やクリックを行い、結果を確認するためのブラウザ操作CLI。
- **主な特徴**：画面のアクセシビリティ情報を短いテキストと参照番号にし、観察と操作を繰り返す。セッション管理、スクリーンショット、MCP接続などを備える。Rust製でApache-2.0。[README](https://github.com/vercel-labs/agent-browser#readme)
- **想定用途・対象者**：フォーム入力、Web画面の動作確認、不具合の再現、確認用スクリーンショットの取得をAIへ任せたい開発者とテスト担当者。
- **その他特筆事項**：画面が変わった後は参照番号を取り直す。見えない・無効・他の要素に覆われた対象へのクリックは失敗させる設計で、操作後の値や保存結果の確認も必要。総スター52,646（今週+3,429）。
- **トレンド入りの理由**：11月13日（日本時間）のv0.43.0で、名前が空または重複する操作対象へ補足情報を付ける機能と、Modern Web Guidanceを使うスキルを追加した。対象の見分けやすさと、Web標準の助言から確認までをつなぐ変更は背景として考えられる。掲載との直接の因果は未確認。[公式リリース](https://github.com/vercel-labs/agent-browser/releases/tag/v0.43.0)

### 15. openai/codex-security

- **リンク**：[https://github.com/openai/codex-security](https://github.com/openai/codex-security)
- **概要・目的**：コードの脆弱性候補を見つけ、調査、修正案の作成、修正済み内容の検証まで進めるCodex Securityのワークフロー、CLI、SDK。
- **主な特徴**：リポジトリ・パス・Git差分の調査、候補の検証、脅威モデルと報告書の保存、重複整理、SARIFなどへの出力、CIでの実行を扱う。CLIとTypeScript SDKを提供し、コードはApache-2.0。[README](https://github.com/openai/codex-security#readme)、[ライセンス](https://github.com/openai/codex-security/blob/main/LICENSE)
- **想定用途・対象者**：自社コードの脆弱性を調べる開発者とセキュリティ担当者。調査結果を修正や課題管理までつなぐ工程を整えたいチーム。
- **その他特筆事項**：利用するモデルや認証、費用、調査対象の送信範囲を確認する。一部の要求・保護された発見事項にはTrusted Access for Cyberが必要。調査完了の報告でも対象外や検証できなかった範囲を読む。総スター14,107（今週+2,531）。
- **トレンド入りの理由**：OpenAIは3月6日の研究プレビュー発表で、コードの前提理解、自動検証、修正案を組み合わせる方針を説明した。現行リポジトリはその作業をCLIやSDKから自動化する経路も提供する。診断と修正をつなぐ用途は注目背景と考えられるが、3月の発表を今週の新規公開とは扱わず、今週の直接要因は未確認。[公式発表](https://openai.com/index/codex-security-now-in-research-preview/)

### 16. dream-num/univer

- **リンク**：[https://github.com/dream-num/univer](https://github.com/dream-num/univer)
- **概要・目的**：自分のWebアプリへ表計算や文書の編集機能を組み込み、業務データやAIと接続するためのOffice SDKの基盤。
- **主な特徴**：表・文書の編集、数式、描画、プラグイン、コマンド、履歴操作、外部アプリ向けAPIを提供する。このリポジトリのオープンソース部分はApache-2.0。[README](https://github.com/dream-num/univer#readme)
- **想定用途・対象者**：ブラウザ内で編集できる管理表、帳票、分析画面を作る開発者。AIが提案した変更を、人が内容を確認しながら直す画面の構築にも関係する。
- **その他特筆事項**：Office SDK全体の機能がこのリポジトリに含まれるわけではない。商用Web拡張、Server SDK、AI SDKの追加機能は別配布・別ライセンス。Excel等との互換性は実際の入力ファイルで確認する。総スター29,875（今週+5,845）。
- **トレンド入りの理由**：公式1.0発表では、表計算を含む複数の編集機能を、共通のプラグインとコマンド体系でアプリへ組み込む構成を説明した。業務アプリに編集とAI支援を組み込みたい需要は背景として考えられる。ただしSDK全体の発表と無料公開部分は区別し、今週の増加との直接の因果は未確認。[公式1.0発表](https://docs.univer.ai/blog/univer-1-0)

レビュー対象16件／サマリー完成16件。
