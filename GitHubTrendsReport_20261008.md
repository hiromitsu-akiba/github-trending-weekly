---
layout: default
title: "GitHubトレンドリポジトリ レビュー(週間: 2026年10月8日時点)"
---

# GitHubトレンド週間レビュー（2026年10月8日時点）

## 全体トレンドの概観

今週の週間トレンド12件のうち7件がAIエージェント関連で、焦点は「エージェント単体の賢さ」から「エージェントを動かす周辺基盤」に移っている。複数のClaude Code・Codexをチームとして束ねるopenrig、エージェントをカーネルレベルで隔離するNVIDIAのOpenShell、セッション間で記憶を引き継ぐclaude-mem、Web全体を読ませるAgent-Reach、エージェント拡張の配布形式を定めるCursorのplugins仕様が並んだ。動画生成もエージェント向けに作り直されており、HeyGenのhyperframesは「HTMLを書けば動画になる」形でエージェントに動画制作を任せる。

AI以外では、PS5実行ファイルをPCネイティブに変換するAnyPS5（今週+6,075スター）と、サブスク不要のセルフホスト筋トレ記録openGym（+4,906）が大きく伸びた。どちらも「既存の囲い込みから手元に取り戻す」志向で、ターミナル動画ダウンローダーyoinksも同じ流れにある。研究系ではDeepSeek-V4の基盤となったGPUカーネルDSLのtilelangと、SIGGRAPH Asia 2026採択のUniMateが入った。

## リポジトリ別サマリー

### 1. [mvschwarz / openrig](https://github.com/mvschwarz/openrig)
- **概要・目的**: Claude Code、Codex、Piを役割付きの常駐チームとして動かすマルチエージェント基盤。ユーザーはリードエージェントとだけ話し、専門エージェントへ仕事が振り分けられる。
- **主な特徴**: TypeScript製CLI（npm: @openrig/cli）。チーム構成をYAML（RigSpec）で定義し1コマンドで起動。SQLiteで状態を永続化し、tmux上で各エージェントが別ターミナルで動く。MCPサーバーとTUIも同梱。Apache-2.0。
- **想定用途・対象者**: 数週間〜数か月続く開発を複数エージェントで回したい開発者・チーム。
- **その他特筆事項**: セットアップ時にプロバイダのhooksやワークスペース信頼設定を書き換えるため、公式ドキュメントは事前バックアップを推奨している。総スター5,774、今週+2,912。
- **トレンド入りの理由**: 2026年10月4日にv0.6.5をリリースし、24時間で248スターを獲得したと報じられた。作者は「1つのハーネス内のサブエージェントより、得意分野の違うClaudeとCodexをまたいでスケールさせる方が効く」と主張しており、この設計思想が注目された（[aitoolly](https://aitoolly.com/ai-news/article/2026-10-03-openrig-unveiled-multi-agent-runtime-framework-unifying-claude-code-and-codex-into-a-single-collabor)、[Zendot](https://zendot.org/en/posts/mvschwarz-openrig)）。

### 2. [boykopovar / AnyPS5](https://github.com/boykopovar/AnyPS5)
- **概要・目的**: PS5の実行ファイルをLinux・Windowsのネイティブ実行形式へ自動変換するツール。エミュレーターではなく変換レイヤーとして動く。
- **主な特徴**: C++製。PS5がAMD Zen 2（x86-64）である点を利用し、リリンカーで実行形式を変換、システムprxライブラリを独自実装で差し替え、シェーダーはVulkan用SPIR-Vに再コンパイルする。Intel CPU向けの命令置換オプションあり。GPL-2.0。
- **想定用途・対象者**: ゲーム互換レイヤーやリバースエンジニアリングに関心のある開発者・研究者。
- **その他特筆事項**: 開発初期段階で、一部タイトルがメニュー到達やゲームプレイまで動いた段階。一般向けの安定ビルドは未公開。未対応の状態では意図的に例外終了する設計。総スター10,495、今週+6,075（今週の増加数で2位）。
- **トレンド入りの理由**: Tom's Hardwareが「エミュレーションを捨て、Proton的なバイナリ変換でPS5ゲームをPCで動かす」と報じ、話題が拡散した。フォークのRyty（PS4対応、macOS実験対応）も派生している（[Tom's Hardware](https://www.tomshardware.com/video-games/playstation/open-source-anyps5-dumps-emulation-to-run-playstation-5-console-games-natively-on-pc-amd-zen-2-architecture-enables-proton-like-binary-translation-for-windows-and-linux)）。

### 3. [heygen-com / hyperframes](https://github.com/heygen-com/hyperframes)
- **概要・目的**: HTML・CSS・アニメーションからMP4を決定的にレンダリングするHeyGen製の動画フレームワーク。AIエージェントが動画を書くことを前提に設計。
- **主な特徴**: 1本の動画を1つのindex.htmlで表し、data-start／data-duration属性で時間軸を指定。ヘッドレスChromeでフレーム単位に描画しFFmpegで書き出すため、マシン性能に関係なく同じ出力になる。GSAP、Lottie、Three.js、WebGLシェーダーに対応。Apache-2.0。
- **想定用途・対象者**: プロダクト紹介動画やSNS動画をエージェントに作らせたい開発者・マーケター。Remotion（React記述、ソース公開ライセンス）の代替を探す人。
- **その他特筆事項**: Claude Code等に読み込ませるスキルを同梱し、企画からレンダリングまでの手順をエージェントに教えられる。tldrawやTanStackが採用。総スター58,524、今週+3,908。
- **トレンド入りの理由**: 2026年4月の公開後も伸び続けており、9月11日にHeyGenがリアルタイムアバター基盤LiveAvatarをOSS化し、そのライブオーバーレイにhyperframesを使ったことで再注目された（[HeyGen Help](https://help.heygen.com/en/articles/15001510-hyperframes-x-heygen)、[The Menon Lab](https://themenonlab.blog/blog/heygen-hyperframes-video-as-code)）。

### 4. [cursor / plugins](https://github.com/cursor/plugins)
- **概要・目的**: Cursorのプラグイン仕様と公式プラグイン集。プラグインはMCPサーバー、スキル、サブエージェント、ルール、hooksを1パッケージにまとめる。
- **主な特徴**: 各プラグインは`.cursor-plugin/plugin.json`を持ち、ルートの`marketplace.json`で複数プラグインを1リポジトリから配布できる。業界標準のAgent Plugins形式とも互換。マーケットプレイス掲載は全件手動レビューかつOSS必須。
- **想定用途・対象者**: Cursorの拡張を作る開発者、社内向けプラグインを配布したいTeams／Enterprise管理者。
- **その他特筆事項**: Teamsプランは1つ、Enterpriseは無制限にチーム専用マーケットプレイスを持てる。総スター10,252、今週+1,109。
- **トレンド入りの理由**: Cursor 2.5でプラグイン機能とマーケットプレイスが導入され、仕様リポジトリが参照元として集中的に見られている。Claude Codeのプラグインと同じくスキルやhooksを束ねる形式で、エージェント拡張の配布形式が各社で揃いつつある点も関心を集めた（[Cursor Blog](https://cursor.com/blog/marketplace)、[Cursor Docs](https://cursor.com/docs/plugins)）。

### 5. [NVIDIA / OpenShell](https://github.com/NVIDIA/OpenShell)
- **概要・目的**: 自律AIエージェントを安全に実行するためのサンドボックス・ランタイム。NVIDIA Agent Toolkitの一部。
- **主な特徴**: Rust製。Landlock LSMでファイルアクセス、seccomp BPFでシステムコールを制限し、外向き通信はすべてYAMLポリシーで検査。エージェントには本物の認証情報を渡さず、許可された宛先への通信時だけ付与する。ポリシー変更は形式検証で危険な権限拡大を検出し人間のレビューに回す。Apache-2.0。
- **想定用途・対象者**: 社内でエージェントを本番運用したい企業のセキュリティ・基盤チーム。
- **その他特筆事項**: Cisco、CrowdStrike、Google Cloud、Microsoft Securityなどとポリシー管理で連携。対応OSはLinux、Apple Silicon macOS、WSL 2（実験的）。総スター15,291、今週+3,690。
- **トレンド入りの理由**: 0.1.x系で安定版リリースのサイクルに入り、新しい隔離プリミティブと拡張点が追加されたとNVIDIAが発表した。プロンプトでの行動制約ではなく実行環境側で制約する方式が、エージェント運用のセキュリティ課題への回答として評価されている（[NVIDIA Blog](https://blogs.nvidia.com/blog/secure-autonomous-ai-agents-openshell/)、[NVIDIA Docs](https://docs.nvidia.com/openshell/about/overview)）。

### 6. [Panniantong / Agent-Reach](https://github.com/Panniantong/Agent-Reach)
- **概要・目的**: AIエージェントにTwitter、Reddit、YouTube、GitHub、Bilibili、小紅書など13プラットフォームの閲覧・検索能力を与えるCLI。有料APIを使わない。
- **主な特徴**: Python製、MIT。自身はラッパーではなく「インストーラー兼診断ツール」で、Jina Reader、yt-dlp、gh CLIなど無料の既存ツールを選定・設定し、エージェントはそれらを直接呼ぶ。`agent-reach doctor`で各チャネルの稼働を確認できる。
- **想定用途・対象者**: Claude Code、Cursor、OpenClaw等でリサーチ系エージェントを作る開発者。
- **その他特筆事項**: Facebook・InstagramはChromeのログイン状態を再利用する仕組みのため、各サービスの利用規約と自社のセキュリティポリシーを確認してから使う必要がある。総スター93,216、今週+6,912（今週の増加数で1位）。
- **トレンド入りの理由**: Twitter APIが中程度の利用で月約215ドルかかる一方、本ツールは無料で同等の情報源に届く点が支持されている。スキルとして`npx skills add`で導入できるようになり、ハンズオン記事が相次いで公開された（[AI Frontier Post](https://aifrontierpost.com/articles/agent-reach-hands-on-tutorial/)、[The Menon Lab](https://themenonlab.blog/blog/agent-reach-internet-for-ai-agents)）。

### 7. [thedotmack / claude-mem](https://github.com/thedotmack/claude-mem)
- **概要・目的**: コーディングエージェントのセッション内容を記録・圧縮し、次回セッションに関連文脈を注入する永続メモリ。
- **主な特徴**: Claude Codeのライフサイクルhooks 5種でツール呼び出しやファイル読込を捕捉し、Claude Agent SDKで圧縮してSQLite（全文検索）とChroma（ベクトル検索）に保存。v12.0以降は記録済みファイルの再読込をブロックし、保存済みの要約で代替してトークンを節約する。データはすべてローカル。
- **想定用途・対象者**: Claude Code、Codex、Gemini、Copilot等で長期案件を進める開発者。
- **その他特筆事項**: `npm install -g`ではhooksが登録されず動かないので、プラグインとしての導入が必須。総スター97,700、今週+2,607。
- **トレンド入りの理由**: 約7か月で259リリースという速い更新が続き、対応エージェントがClaude Code以外に広がった。2026年4月の5.4万スターから約10万スターへ伸び、メモリ系プラグインの定番として紹介記事が増えている（[Augment Code](https://www.augmentcode.com/learn/claude-mem-65k-stars)、[DataCamp](https://www.datacamp.com/tutorial/claude-mem-guide)）。

### 8. [pablostanley / yoinks](https://github.com/pablostanley/yoinks)
- **概要・目的**: YouTube、X、Instagram、TikTokなど1,800以上のサイトから動画をダウンロードするターミナルアプリ。広告や偽ボタンのあるダウンロードサイトの代替。
- **主な特徴**: TypeScript製、Ink（CLI向けReact）で作ったTUI。URLを貼り解像度か音声のみMP3を選ぶだけ。yt-dlpとffmpegを自動取得するためPython不要。マウス操作やテーマ切替にも対応。MIT。
- **想定用途・対象者**: yt-dlpのオプションを覚えずに使いたい人。スクリプトから呼ぶ用途には向かない。
- **その他特筆事項**: ダウンロード可否は各サイトの利用規約と著作権に従う必要がある。総スター5,094、今週+2,732。
- **トレンド入りの理由**: 作者のPablo Stanley（デザイナーとして著名）が「初めて作ったTUI」としてXで公開し、デザイン性の高いTUIとして拡散した（[Pablo StanleyのX投稿](https://x.com/pablostanley/status/2077840975901380689?lang=en)、[Zendot](https://zendot.org/en/posts/pablostanley-yoinks)）。

### 9. [DuarteSantos8 / openGym](https://github.com/DuarteSantos8/openGym)
- **概要・目的**: セルフホストで運用する筋トレ・体重記録アプリ。アカウント登録、サブスク、広告、テレメトリがない。
- **主な特徴**: JavaScript製PWA。1,324種目のアニメーション付きライブラリ、ボディマップでの部位検索、スーパーセットやドロップセット対応。部位ごとに「鍛えた／疲労中／衰え」を可視化し、FitNotes・Strong・Hevyからインポートできる。パスキーログイン。`docker compose up`で起動。AGPL-3.0。
- **想定用途・対象者**: 自宅サーバーを持つトレーニー、健康データを外部サービスに預けたくない人。
- **その他特筆事項**: サーバー不要のAndroid APK版とブラウザだけで動くデモもある。Kubernetesマニフェストも提供。総スター6,869、今週+4,906。
- **トレンド入りの理由**: 7月20日のv1.0.0から短期間でv1.3.9まで更新を重ね、主要筋トレアプリからの移行機能とKubernetes対応が揃ったことで、セルフホスト系コミュニティで広く共有された（[OSS Insight](https://ossinsight.io/analyze/DuarteSantos8/openGym)、[CHANGELOG](https://github.com/DuarteSantos8/openGym/blob/main/CHANGELOG.md)）。

### 10. [tile-ai / tilelang](https://github.com/tile-ai/tilelang)
- **概要・目的**: GPU・CPU・アクセラレータ向けの高性能カーネルをPythonで書くためのドメイン固有言語。
- **主な特徴**: スレッド階層、共有メモリ、ベクトル化を明示的に制御しつつ、最適化済みのGPUコードへコンパイルする。約80行のPythonでDeepSeekのMLAデコードカーネルを書くとH100でFlashMLA並みの性能が出たという報告がある。
- **想定用途・対象者**: LLMの学習・推論を高速化する研究者、カーネルエンジニア。
- **その他特筆事項**: 論文「TileLang: A Composable Tiled Programming Model for AI Systems」（arXiv 2504.17577）。総スター8,471、今週+639。
- **トレンド入りの理由**: DeepSeek-V4の論文が、数百のATen演算子を置き換える融合カーネルをTileLangで作ったと明記した。さらに9月30日、TileLangで書かれたDeepSeekのTileKernelsがHuawei Ascendに対応し、同じAPIでNVIDIAとAscendの両方を動かせるようになったことで関心が高まった（[DeepSeek-V4論文](https://arxiv.org/pdf/2606.19348)、[TileKernels](https://github.com/deepseek-ai/TileKernels)）。

### 11. [HunxByts / GhostTrack](https://github.com/HunxByts/GhostTrack)
- **概要・目的**: IPアドレス、電話番号、ユーザー名の公開情報を調べるOSINT（公開情報調査）用Pythonツール。
- **主な特徴**: メニュー式でIP追跡（ipwho.is APIで登録地域やISPを表示）、電話番号調査（phonenumbersライブラリで通信事業者・地域・番号種別を判定）、ユーザー名の23以上のSNS存在確認の3機能をまとめる。Linux、Termuxで動く。
- **想定用途・対象者**: OSINTを学ぶセキュリティ学習者、許可を得た調査の補助。
- **その他特筆事項**: 名前に反して電話の現在位置は分からず、IPの位置も登録地にすぎない。READMEで紹介されている連携ツールSeekerは偽サイトで位置情報を取得するもので、本人の同意なく使えば多くの国で違法になる。コミット23件・コントリビューター2名と保守は細い。総スター17,383、今週+1,534。
- **トレンド入りの理由**: OSINT入門ツールとして解説記事やSNS動画で繰り返し取り上げられ、定期的に再浮上している。専門ツール（PhoneInfoga、Sherlock、Maltego）の代替ではなく学習用という評価が一般的（[PyShine](https://pyshine.com/GhostTrack-OSINT-Location-Tracking-Tool/)、[techshali](https://techshali.com/ghosttrack/)）。

### 12. [Friedrich-M / UniMate](https://github.com/Friedrich-M/UniMate)
- **概要・目的**: リグ付き3Dアセットとテキストから、骨格の形を問わずモーションを生成する統一モデル。SIGGRAPH Asia 2026採択論文の公式実装。
- **主な特徴**: トポロジーを考慮した拡散Transformer。関節間の測地距離によるアテンションバイアス、グラフラプラシアンでRoPEを任意の骨格木へ一般化した位置埋め込み、骨格全体の条件付けの3機構を持つ。骨格ごとの再学習や推論時最適化が不要。
- **想定用途・対象者**: ゲーム・映像の3Dアニメーター、モーション生成の研究者。
- **その他特筆事項**: 7,430骨格・13,769クリップ（二足、四足、鳥、海洋生物、昆虫、蛇、関節付き剛体）のデータセットUniML3Dを構築。ただしTruebones由来の動物モーションは再配布不可で各自購入が必要。データは人型に偏っている。Princeton、UC Berkeley、MIT、NTUの共同研究。総スター1,564、今週+716。
- **トレンド入りの理由**: 9月6日に学習・推論コードとHugging Faceのプレビュー重みを公開し、10月5日には任意のGLB／glTF／FBXを取り込める前処理ツールを追加した。自動リギングの次の課題であるモーション生成を汎用化した点が注目された（[arXiv 2609.05415](https://arxiv.org/abs/2609.05415)、[プロジェクトページ](https://linzhanmou.com/unimate/)）。

## サマリー

**対象リポジトリ数: 12件 | サマリー完成: 12件**
