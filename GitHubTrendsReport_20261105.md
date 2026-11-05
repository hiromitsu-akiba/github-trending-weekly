---
layout: default
title: "GitHubトレンドリポジトリ レビュー(週間: 2026年11月5日時点)"
---

# GitHubトレンド週間レビュー（2026年11月5日時点）

## 全体トレンドの概観

コーディングエージェントを継続して使うための環境整備が目立つ。Claude-Memは作業履歴を次の会話へ引き継ぎ、T3 Codeは複数のエージェントをデスクトップやスマートフォンから操作する。WorktrunkとThinkRailはGit worktreeで作業場所を分ける。単発のコード生成から、履歴、並行作業、差分レビューを扱う日常の開発環境へ関心が広がった構成と読める。

画面品質を扱うHallmark、Impeccable、jakubkrehel/skills、Taste Skillも並ぶ。テーマや見た目の指示に加え、既存機能の保持、複数画面幅での描画、アクセシビリティ、検査結果の扱いまで具体化している。ただし、機械的な検査を通過しても、業務画面の使いやすさや説明の正確さは別途確認が必要だ。

週間増分ではT3 Codeが+14,580、Impeccableが+10,921、Claude-Memが+8,822。GhosttyとHyprlandのような端末やデスクトップ基盤も含まれ、AI向けスキルだけではない。用途を選ぶ際は、生成物を改善する道具と、エージェントを動かす環境を分けて検討したい。

## リポジトリ別サマリー

### 1. thedotmack/claude-mem

- **リンク**：[https://github.com/thedotmack/claude-mem](https://github.com/thedotmack/claude-mem)
- **概要・目的**：エージェントのツール利用履歴を記録し、要約と検索を通じて次のセッションへ知識を引き継ぐ永続メモリ。
- **主な特徴**：フック、ローカルworker、SQLite、検索機能を組み合わせる。検索索引、前後の時系列、必要な記録本文の順に情報を読む。現行READMEはApache-2.0と明記。[README](https://raw.githubusercontent.com/thedotmack/claude-mem/HEAD/README.md)
- **想定用途・対象者**：調査や開発を複数日に分け、判断理由や過去の修正を再利用したい開発者。
- **その他特筆事項**：要約用モデルと任意のクラウド同期では送信先を確認したい。記憶の保存と内容の正しさは別問題で、機密情報の除外と誤った記録の訂正が必要。総スター112,823（今週+8,822）。
- **トレンド入りの理由**：GitHub表示11月2日の[v15.9.0](https://github.com/thedotmack/claude-mem/releases/tag/v15.9.0)ではDevin対応、remote worker設定、記録重複や検索の修正、保存前の秘密情報除去を拡充した。複数環境で履歴を使い続ける用途が注目背景として考えられる。更新とスター増加の直接の因果は未確認。

### 2. Nutlope/hallmark

- **リンク**：[https://github.com/Nutlope/hallmark](https://github.com/Nutlope/hallmark)
- **概要・目的**：コーディングエージェントへWebページのデザイン手順と品質基準を渡すスキル。目的に沿うページ構成と、定型的な装飾の抑制を扱う。
- **主な特徴**：現行v2のREADMEは50テーマ、独自方向の指定、再設計と監査を説明する。静的検査に加え、ブラウザで8種類の幅を確認し、別のレビュー工程を置く。MIT。[README](https://raw.githubusercontent.com/Nutlope/hallmark/HEAD/README.md)
- **想定用途・対象者**：サービス紹介ページや勉強会サイトを作る開発者。既存ページを改修する際の確認手順にも使える。
- **その他特筆事項**：再設計ではリンク、フォーム、処理、見出しの保持を検査する。ブラウザ検査にはChromeとpuppeteer-coreが必要。写真は素材ごとのライセンスと表示義務が残る。総スター47,901（今週+7,622）。
- **トレンド入りの理由**：[公式リポジトリ](https://github.com/Nutlope/hallmark)では、見た目に加え、動かないフォームや架空の事実を出荷しない基準を前面に出す。生成ページを実際に使える状態へ近づける手順が関心を集めた背景と考えられる。今週の特定の公開日や告知との関係は未確認。

### 3. pingdotgg/t3code

- **リンク**：[https://github.com/pingdotgg/t3code](https://github.com/pingdotgg/t3code)
- **概要・目的**：ローカルのコーディングエージェントを、Web、Electron製デスクトップアプリ、モバイルアプリから操作する管理画面。
- **主な特徴**：Claude Code、Codex、Cursor、OpenCodeなどの既存環境と認証を利用する。会話、ソース管理、遠隔接続、プロジェクト設定の操作をまとめる。[README](https://raw.githubusercontent.com/pingdotgg/t3code/HEAD/README.md)
- **想定用途・対象者**：複数エージェントや複数の作業を切り替え、別の端末からも進行状況を確認したい開発者。
- **その他特筆事項**：利用するproviderの導入と認証が必要。作者は初期段階で不具合があると明記する。管理画面を追加しても、実行権限や通信経路の確認は省けない。総スター46,565（今週+14,580）。
- **トレンド入りの理由**：GitHub表示11月4日の[v0.1.7](https://github.com/pingdotgg/t3code/releases/tag/v0.1.7)は管理ポリシー、単発スケジュール、子エージェントの承認操作、会話リンクを追加した。個人のCLI操作から日常運用へ広げる機能が注目背景として考えられる。掲載順とは別に、今回の週間増分は対象内で最大。

### 4. pbakaus/impeccable

- **リンク**：[https://github.com/pbakaus/impeccable](https://github.com/pbakaus/impeccable)
- **概要・目的**：既存UIのレビュー、改善指示、定型的なデザインの検出をコーディングエージェントへ追加するツール群。
- **主な特徴**：24コマンドと62の決定的な検出ルールを説明する。PRODUCT.mdとDESIGN.mdへ用途とデザイン規約を保存し、ソース検査や描画後の検査に利用する。Apache-2.0。[README](https://raw.githubusercontent.com/pbakaus/impeccable/HEAD/README.md)
- **想定用途・対象者**：業務画面のレビュー、試作ページの仕上げ、UI変更をCIで点検したい開発者やテスト担当者。
- **その他特筆事項**：ソース検査とURLの描画検査では確認できる内容が異なる。現行READMEはlive modeのApplyで承認を迂回するCLIが起動する条件も説明しており、実行設定の確認が必要。総スター102,790（今週+10,921）。
- **トレンド入りの理由**：[公式更新履歴](https://impeccable.style/changelog/)の10月26日付v4.8.0では、GitHub Actionsの検出結果をPR上へ注記し、配布エンジンのダイジェストを検証する機能を追加した。UIの助言を変更レビューへ組み込める点が注目背景として考えられる。前週に続く掲載で、今週の新規公開を意味しない。

### 5. obra/superpowers

- **リンク**：[https://github.com/obra/superpowers](https://github.com/obra/superpowers)
- **概要・目的**：要件確認、計画、実装、テスト、レビュー、完了確認をスキルとしてまとめた、エージェント向けソフトウェア開発手順。
- **主な特徴**：テスト駆動開発、原因調査、Git worktree、計画に沿う実行を組み合わせる。複数のエージェント環境向け導入経路を用意する。MIT。[README](https://raw.githubusercontent.com/obra/superpowers/HEAD/README.md)
- **想定用途・対象者**：実装を急いで要求を取り違える問題や、修正後の検証漏れを減らしたい開発者。
- **その他特筆事項**：自動発火するスキルは既存の案件ルールと重なるため、質問や承認の頻度も含めて確認したい。手順の導入だけで品質向上を保証するものではない。総スター312,432（今週+5,565）。
- **トレンド入りの理由**：GitHub表示11月3日の[v7.0.2](https://github.com/obra/superpowers/releases/tag/v7.0.2)は、実装内容を変えない不要な質問を減らし、Windowsを含む起動フックや実行補助スクリプトを修正した。開発手順を厳密にするだけでなく、実際の会話や作業で使い続けやすくする改善が背景候補。直接要因は未確認。

### 6. anthropics/skills

- **リンク**：[https://github.com/anthropics/skills](https://github.com/anthropics/skills)
- **概要・目的**：Anthropicが公開するAgent Skillsの実装例。文書、デザイン、開発、業務作業の手順をフォルダ単位で配布する。
- **主な特徴**：SKILL.mdに説明と起動条件を置き、必要なスクリプトや資料を添える。文書処理を含む実装例とテンプレートを提供する。[README](https://raw.githubusercontent.com/anthropics/skills/HEAD/README.md)
- **想定用途・対象者**：資料作成や定型業務を再利用可能な手順へまとめたい開発者、既存スキルの構成を学びたい利用者。
- **その他特筆事項**：多くはApache-2.0だが、docx、pdf、pptx、xlsxはsource-availableとして公開され、同一条件ではない。各フォルダの利用条件を確認する。総スター187,415（今週+3,003）。
- **トレンド入りの理由**：Anthropicは[10月22日の公式発表](https://www.anthropic.com/news/donating-agent-skills-to-the-agentic-ai-foundation)でAgent Skills標準のAAIFへの寄贈を発表した。複数ツールで手順を持ち運ぶ関心の背景になる。ただし寄贈対象の標準と、この実装例リポジトリの個別ライセンスは分けて扱う。掲載への直接の影響は未確認。

### 7. max-sixty/worktrunk

- **リンク**：[https://github.com/max-sixty/worktrunk](https://github.com/max-sixty/worktrunk)
- **概要・目的**：Git worktreeの作成、切り替え、状態確認、片付けを簡略化し、並行する開発作業を管理するCLI。
- **主な特徴**：ブランチ名で作業ディレクトリを指定し、フック、PR切り替え、CI状態の表示、ローカル統合を支援する。MITまたはApache-2.0。[README](https://raw.githubusercontent.com/max-sixty/worktrunk/HEAD/README.md)
- **想定用途・対象者**：機能開発と不具合修正、複数エージェントの変更を別ディレクトリで進めたい開発者。
- **その他特筆事項**：WindowsではWindows Terminalのwtと競合するためgit-wtを使う導入経路がある。削除や統合を伴う操作は、未追跡ファイルを含む保持条件を確認して使いたい。総スター11,010（今週+1,261）。
- **トレンド入りの理由**：[v0.81.0](https://github.com/max-sixty/worktrunk/releases/tag/v0.81.0)はGitHub表示10月20日の更新で、前景フックの入力、任意パスへの作業場所作成、OpenCode 2連携などを拡充した。並行作業を増やした際の準備や後始末を減らす用途が注目背景と考えられる。今週の新規リリースとは扱わない。

### 8. jakubkrehel/skills

- **リンク**：[https://github.com/jakubkrehel/skills](https://github.com/jakubkrehel/skills)
- **概要・目的**：UI、文字組み、色、レイアウト、アクセシビリティ、画面内の文章を改善するエージェント向けスキル集。
- **主な特徴**：画面全体の優先順位付きレビューに加え、変更差分のレビュー、状態一覧、部品の負荷条件確認、複数案の比較を個別の手順に分ける。[README](https://raw.githubusercontent.com/jakubkrehel/skills/HEAD/README.md)
- **想定用途・対象者**：UIテスト観点の洗い出し、エラー文言の改善、長い日本語や拡大表示を含む画面確認を行う開発者とテスト担当者。
- **その他特筆事項**：WCAG 2.2を扱うスキルを含むが、導入だけで適合を保証しない。実際のキーボード操作や読み上げを確認する必要がある。総スター10,806（今週+1,865）。
- **トレンド入りの理由**：[公式README](https://github.com/jakubkrehel/skills)は見た目の微調整と、変更で発生した問題のレビューを分けて提供する。生成後の画面品質を検証する関心が、前週からの継続掲載の背景と考えられる。特定の今週の告知との対応は未確認。

### 9. JetBrains/thinkrail

- **リンク**：[https://github.com/JetBrains/thinkrail](https://github.com/JetBrains/thinkrail)
- **概要・目的**：piコーディングエージェントへエディタ、会話、差分、作業場所、仕様書の画面を加えるIDE。JetBrainsのincubatorプロジェクト。
- **主な特徴**：Git worktreeで分けた作業場所と、コード横のSPEC.md群で継続する仕様知識を管理する。MCP、複数の会話、日本語UIを備える。Apache-2.0。[README](https://raw.githubusercontent.com/JetBrains/thinkrail/HEAD/README.md)
- **想定用途・対象者**：仕様と実装の対応を保ちながら、エージェントの変更を目で確認したい開発者。
- **その他特筆事項**：モデルproviderの認証が必要。アプリの利用計測とproviderへのデータ送信を区別して確認する。仕様書を残しても、コードとの一致はレビューが必要。総スター7,596（今週+3,031）。
- **トレンド入りの理由**：[11月1日の0.3.1公式記事](https://thinkrail.ai/blog/thinkrail-0-3-1-release/)は横断検索、独自モデルサーバーの設定、piパッケージ管理を紹介した。既存のモデル環境やスキルを画面から扱いやすくする動きが注目背景として考えられる。独自サーバー対応はOpenAI chat-completions互換に限定される。

### 10. ghostty-org/ghostty

- **リンク**：[https://github.com/ghostty-org/ghostty](https://github.com/ghostty-org/ghostty)
- **概要・目的**：macOSやLinuxで使う端末エミュレータと、アプリへ端末機能を組み込むためのlibghosttyを開発するプロジェクト。
- **主な特徴**：OSに合わせたGUI、タブと分割表示、画像プロトコルなどの端末機能を実装する。端末状態を扱うlibghostty-vtはGUIと別のリリース系列を持つ。[README](https://raw.githubusercontent.com/ghostty-org/ghostty/HEAD/README.md)
- **想定用途・対象者**：端末を長時間使う開発者、アプリへ端末表示を組み込みたい開発者。
- **その他特筆事項**：ライブラリのWindows対応と、Ghostty GUIの対応OSを混同しない。クラッシュ記録は自動送信されないが、送る際にはメモリ内の機密情報を含む可能性を確認する。総スター63,544（今週+738）。
- **トレンド入りの理由**：[10月27日公開の1.4.0](https://ghostty.org/docs/install/release-notes/1-4-0)はKitty画像機能、スクロール履歴の圧縮、SSH連携、描画と端末処理を改善した。端末機能を広げつつ重い出力の扱いを改善した点が背景候補。公式の性能数値は測定条件付きであり、掲載への直接要因は未確認。

### 11. multica-ai/andrej-karpathy-skills

- **リンク**：[https://github.com/multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills)
- **概要・目的**：KarpathyのLLMコーディングに関する観察を参考に、エージェントの変更範囲と検証手順をまとめたガイドライン。
- **主な特徴**：実装前に考える、単純さを優先する、必要な箇所だけ変える、検証可能な目標で進める、の4原則を記す。MIT。[README](https://raw.githubusercontent.com/multica-ai/andrej-karpathy-skills/HEAD/README.md)
- **想定用途・対象者**：過剰な抽象化、無関係な変更、確認なしの思い込みを減らすため、案件ルールを整えたい開発者。
- **その他特筆事項**：Karpathy本人の公式配布物ではなく、投稿を参考に作者が構成したもの。現行READMEの導入例には旧owner名が残る。総スター229,493（今週+3,808）。
- **トレンド入りの理由**：[公式READMEの4原則](https://github.com/multica-ai/andrej-karpathy-skills)は、依頼に追跡できる差分と、再現テストなどの成功条件を重視する。複雑な実行基盤へ増設しやすい短い指示として継続的に関心を集める背景と考えられる。今週の新しい公式発表は確認できていない。

### 12. hyprwm/Hyprland

- **リンク**：[https://github.com/hyprwm/Hyprland](https://github.com/hyprwm/Hyprland)
- **概要・目的**：LinuxのWayland環境でウィンドウ配置とデスクトップ表示を管理する、動的タイル型コンポジタ。
- **主な特徴**：複数の配置方式、ワークスペース、プラグイン、IPC、即時反映する設定、アニメーションを備える。[README](https://raw.githubusercontent.com/hyprwm/Hyprland/HEAD/README.md)
- **想定用途・対象者**：Linuxの開発環境で、複数ウィンドウや端末の配置と操作を細かく調整したい利用者。
- **その他特筆事項**：Windows向けの画面管理ツールではない。アップグレード時には設定方式や画面共有環境との互換性を確認したい。総スター40,300（今週+1,325）。
- **トレンド入りの理由**：[10月28日の0.57公式発表](https://hypr.land/news/update57/)は、ワークスペース単位の画面共有、ぼかし表現、Lua API拡充を紹介し、旧.conf設定の非対応化も告知した。新機能の評価と設定移行の両方が関心の背景になりうる。スター増加との直接の因果は未確認。

### 13. AgriciDaniel/claude-seo

- **リンク**：[https://github.com/AgriciDaniel/claude-seo](https://github.com/AgriciDaniel/claude-seo)
- **概要・目的**：Claude Code上でWebサイトのSEOとAI検索向けの確認を行い、修正の優先順位をまとめるプラグイン。
- **主な特徴**：26のサブスキルと19の専門エージェントを説明する。技術SEO、コンテンツ、構造化データ、地域検索、EC、AI検索への対応を扱う。公開版はMIT。[README](https://raw.githubusercontent.com/AgriciDaniel/claude-seo/HEAD/README.md)
- **想定用途・対象者**：公開サイトの調査、ページ改修前の点検、提案資料へ載せる改善候補の整理を行う担当者。
- **その他特筆事項**：ページ情報はモデルへ送信される。任意の外部サービスは追加費用や認証が必要。Google APIなしでは一部の評価が推定となり、検索順位やAIからの引用を保証しない。総スター26,651（今週+3,531）。
- **トレンド入りの理由**：[10月22日付v2.5.0の更新履歴](https://raw.githubusercontent.com/AgriciDaniel/claude-seo/HEAD/CHANGELOG.md)では、監査上の指針と精度を修正し、Claude Desktopの導入を復旧した。SEOを優先順位付きの作業へまとめる用途が継続掲載の背景候補。今週の新規公開としては扱わず、直接の流入要因は未確認。

### 14. calesthio/OpenMontage

- **リンク**：[https://github.com/calesthio/OpenMontage](https://github.com/calesthio/OpenMontage)
- **概要・目的**：調査、脚本、素材、編集、合成の手順をコーディングエージェントへ渡し、動画制作を進めるシステム。
- **主な特徴**：YAMLの制作工程とMarkdownのスキル、Pythonのツールを組み合わせる。Remotion、HyperFrames、FFmpegなどを使い、素材の承認、状態保存、費用記録、レンダリング後の確認を行う。AGPLv3。[README](https://raw.githubusercontent.com/calesthio/OpenMontage/HEAD/README.md)
- **想定用途・対象者**：勉強会の解説動画、ソフトウェアの操作紹介、既存動画の短尺化を試したい制作者や開発者。
- **その他特筆事項**：実行する工程により依存関係、モデル費用、GPU要件が異なる。素材利用条件と原稿の出典確認も必要。README内の作例費用を一般的な制作費とは扱わない。総スター76,509（今週+3,743）。
- **トレンド入りの理由**：[公式README](https://github.com/calesthio/OpenMontage)では、生成素材だけでなく実写の検索と編集、Backlotの制作状況表示、場面ごとの承認を紹介する。動画制作を確認可能な工程へ分ける使い方が背景候補。特定の今週の発表と増加の対応は未確認。

### 15. Leonxlnx/taste-skill

- **リンク**：[https://github.com/Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill)
- **概要・目的**：企業やサービスのWebサイトを作るエージェント向けスキル。ページの構成、素材、デザイン規約、ブラウザでの確認をまとめる。
- **主な特徴**：現行2.5.0は共通のHTML/CSS基盤を採用し、事業の種類に応じて画像や効果を選ぶ。4種類の画面幅で整合性を確認する。MIT。[README](https://raw.githubusercontent.com/Leonxlnx/taste-skill/HEAD/README.md)
- **想定用途・対象者**：企業サイト、製品紹介、店舗サイトの制作を試す開発者。業務アプリの汎用設計規約とは用途を分けたい。
- **その他特筆事項**：Node 22以降とChrome系ブラウザが必要。写真やブランド素材の条件は別に確認する。旧2.1系のスクリプトを前提にした導入や検査手順は再確認が必要。総スター110,047（今週+5,935）。
- **トレンド入りの理由**：[更新履歴](https://github.com/Leonxlnx/taste-skill/blob/main/CHANGELOG.md)は11月5日付2.5.0で企業サイト向けの再構成、100超のブラウザ検査、スマートフォンや動きを減らす設定への代替表示を説明する。生成結果を規約と実測で確認する方向の具体化は注目点。ただし同日付の変更を、それ以前の週間増加の原因とは断定できない。

レビュー対象15件／サマリー完成15件。
