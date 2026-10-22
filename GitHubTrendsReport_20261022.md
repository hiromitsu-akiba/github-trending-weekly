---
layout: default
title: "GitHubトレンドリポジトリ レビュー(週間: 2026年10月22日時点)"
---

# GitHubトレンド週間レビュー（2026年10月22日時点）

## 全体トレンドの概観

エージェントの専門知識をスキルとして配り、複数の開発ツールで再利用する動きが目立つ。AnthropicとCursorのプラグイン集、Android公式の開発スキル、科学研究向けのScientific Agent Skills、複数の実行環境へ専門エージェントを配布するwshobson/agentsが並んだ。開発手順だけでなく、製品公式の移行・最適化手順や、研究分野固有の分析手順まで配布対象が広がっている。

長時間の作業を続けるための仕組みも増えている。context-modeはツール出力を検索可能な形へ整理し、ai-memoryはエージェントを切り替えても判断や作業を引き継ぐ。RufloとOrcaは複数エージェントの実行・監視、OpenCodeは開発作業を行う実行環境を担う。モデルの選択に加え、記憶、コンテキスト、権限、作業場所の管理が導入時の検討対象になっている。

REAは今週+129,417スターで引き続き突出する。Ghidraも掲載され、既存ソフトウェアを解析してエージェントにつなぐ分野への関心が続く。一方、VoiceStudioは音声、HyperFramesは動画、text-to-cadは設計データを扱い、成果物を作る用途も残る。スター増加の大きさと、導入後の品質・安全性・費用対効果は分けて評価したい。

## リポジトリ別サマリー

### 1. morluto/rea

- **リンク**：[https://github.com/morluto/rea](https://github.com/morluto/rea)
- **概要・目的**：既存アプリ、ネイティブバイナリー、実行時の動作をAIエージェントから調査するための、リバースエンジニアリング用MCPサーバーとCLI。
- **主な特徴**：Hopper・Ghidra・IDAなどの解析エンジンに接続し、JavaScript・Electron・.NET・Androidなども扱う。解析結果に根拠と制約を付け、CLIとMCPで共通の手順を使う。独自コードはMIT、外部ツールや第三者コードの条件は別。[README](https://raw.githubusercontent.com/morluto/rea/HEAD/README.md)
- **想定用途・対象者**：ソースがないソフトの動作調査、互換性調査、許可されたセキュリティ解析を行う開発者・解析担当者。
- **その他特筆事項**：解析エンジン、OS、対象形式によって利用可能な機能が異なる。mainの修正と公開パッケージへの反映は区別が必要。総スター357,692（今週+129,417）。
- **トレンド入りの理由**：10月17日、作者はVS Code向けMCPスキーマ不具合について、mainで26件の関連検証を通過したと報告した。同時に、当該修正は公開済み6.5.0には含まれず、VS Code本体での実行確認もしていないと明記している。解析能力の拡張に加え、実際の接続先で使うための互換性改善が進む点は注目材料。ただし、この修正が週間増加の直接要因とは確認できない。[作者の不具合対応](https://github.com/morluto/rea/issues/4736)

### 2. anthropics/claude-plugins-official

- **リンク**：[https://github.com/anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)
- **概要・目的**：Anthropicが管理するClaude Code向けプラグインディレクトリ。自社製プラグインと、パートナー・コミュニティ製プラグインの導入先をまとめる。
- **主な特徴**：コマンド、エージェント、スキル、MCP設定などをプラグインとして配布する。READMEは名前変更時の移行情報や、専用manifestを持たないスキル集の登録方法も案内する。ライセンスは各プラグイン単位で確認する。[README](https://raw.githubusercontent.com/anthropics/claude-plugins-official/HEAD/README.md)
- **想定用途・対象者**：Claude Codeの利用者、社内で導入候補を整理する管理者、再利用可能な開発支援機能を公開する作者。
- **その他特筆事項**：公式ディレクトリに載っていても、含まれるMCPサーバーやソフトウェアの将来の動作まで保証されるわけではない。第三者製の内容と権限は個別確認が必要。総スター43,633（今週+5,703）。
- **トレンド入りの理由**：公式READMEでは、自社製と外部製の区分に加え、スキルだけのリポジトリを配布できる登録方法まで整備されている。個別の設定を探してコピーする手間を減らし、拡張を継続配布する入口として関心を集める背景が考えられる。今週固有の新規発表とスター増加の因果は未確認。[公式ディレクトリの説明](https://github.com/anthropics/claude-plugins-official#skill-bundle-plugins)

### 3. K-Dense-AI/scientific-agent-skills

- **リンク**：[https://github.com/K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills)
- **概要・目的**：科学研究で使う分析・データ取得・検証・文章作成の手順を、AIエージェント向けのスキルとして共有するライブラリー。
- **主な特徴**：現行READMEは177スキルと100以上の科学データベースを案内する。生物、化学、物理、工学、統計、科学的文章作成などを扱い、Agent Skills対応の複数製品で利用できる。リポジトリはMITだが、個々のスキルのlicense欄と依存先の条件も確認する。[README](https://raw.githubusercontent.com/K-Dense-AI/scientific-agent-skills/HEAD/README.md)
- **想定用途・対象者**：専門分野の手順をエージェントへ渡したい研究者・分析担当者。文献調査、統計、図表、根拠を追えるレポート作成を扱う人。
- **その他特筆事項**：関連論文は163手順時点の資料構成を評価しており、現行READMEの177件とは時点が異なる。論文はタスク単位の性能評価やスキル選択率を報告していないため、実務精度の保証としては使えない。総スター53,578（今週+4,719）。
- **トレンド入りの理由**：8月30日公開・9月2日改訂の関連論文は、専門的な手続き知識を必要時だけ読み込む設計を説明する。現行READMEでは旧称Claude Scientific Skillsからの改称と、Claude以外への対応拡大も案内されている。専門知識をモデルへの追加学習なしで共有する手段として関心の背景が考えられる。これらを今週の新規公開とは扱わない。[著者の論文](https://arxiv.org/abs/2609.00065)

### 4. ruvnet/ruflo

- **リンク**：[https://github.com/ruvnet/ruflo](https://github.com/ruvnet/ruflo)
- **概要・目的**：Claude CodeやCodexの周囲に、タスク配分、複数エージェントの協調、記憶、監視を加える実行管理基盤。旧称はClaude Flow。
- **主な特徴**：CLI・MCP、専門エージェント、記憶検索、コンソール、ポリシーを組み合わせる。Claude Code専用のconsole・modsと、他製品にも接続可能なMCP経路を区別する。ライセンスはMIT。[README](https://raw.githubusercontent.com/ruvnet/ruflo/HEAD/README.md)
- **想定用途・対象者**：複数のエージェントへ開発・調査を分担させ、作業状態や使用量もまとめて確認したい開発者。
- **その他特筆事項**：機能数や概念図は、実際の仕事が完了した証拠にはならない。フック対応と利用できる機能は接続する製品ごとに異なる。総スター78,211（今週+3,590）。
- **トレンド入りの理由**：公式変更履歴の10月14日版3.56.10では、TUIコンソール表示の拡充、実装スキルの任意導入化、MCPの作業ディレクトリや重複プロセスの修正を確認できる。協調機能の多さだけでなく、監視と導入範囲の調整を整備する動きが注目材料。10月14日の変更を今週の発表とはせず、掲載の直接要因は未特定。[公式変更履歴](https://github.com/ruvnet/ruflo/blob/main/CHANGELOG.md)

### 5. android/skills

- **リンク**：[https://github.com/android/skills](https://github.com/android/skills)
- **概要・目的**：Android開発の公式な知識・作業手順を、AIエージェントが参照できるモジュール化されたスキルとして提供するGoogleのリポジトリ。
- **主な特徴**：Android CLIからの追加・更新と、Claude Code・Codex向けプラグイン導入を案内する。AGP 9移行、XMLからComposeへの移行、Navigation 3、edge-to-edge、R8の設定確認などを扱う。Apache-2.0。[README](https://raw.githubusercontent.com/android/skills/HEAD/README.md)
- **想定用途・対象者**：Androidアプリの保守、移行、最適化をエージェントと進める開発者・モバイル開発チーム。
- **その他特筆事項**：READMEでは、評価でLLMが苦手と分かった用途・作業手順を重点対象にすると説明する。導入後もビルド、端末動作、移行前後の振る舞いを検証する必要がある。総スター9,147（今週+1,332）。
- **トレンド入りの理由**：公式文書が、製品の新しい知識をAgent Skills標準で複数のAIツールへ渡す手順と、具体的な移行・性能確認の用途を公開している。モデルの既存知識が追い付かないAPIや設定を、製品提供元の手順で補える点が関心の背景と考えられる。今週の単独発表や公開日は特定できていない。[Android公式文書](https://developer.android.com/tools/agents/android-skills)

### 6. NationalSecurityAgency/ghidra

- **リンク**：[https://github.com/NationalSecurityAgency/ghidra](https://github.com/NationalSecurityAgency/ghidra)
- **概要・目的**：米NSAが開発・保守する、コンパイル済みソフトウェアを調べるリバースエンジニアリング基盤。
- **主な特徴**：逆アセンブル、逆コンパイル、グラフ、スクリプトによる拡張、対話操作・自動処理に対応する。多様な命令セットと実行形式を扱い、Windows・macOS・Linuxで利用できる。[README](https://raw.githubusercontent.com/NationalSecurityAgency/ghidra/HEAD/README.md)
- **想定用途・対象者**：マルウェア解析、脆弱性調査、既存バイナリーの構造・挙動を調べる研究者・開発者。
- **その他特筆事項**：main相当の開発文書と、導入する配布版の要件は分けて確認する。READMEは一部バージョンの既知脆弱性について公式アドバイザリーの確認を求めている。総スター92,626（今週+5,769）。
- **トレンド入りの理由**：公式配布先の12.1.4は9月21日公開と表示され、今週の新規リリースではない。一方、REAはGhidraをネイティブ解析の接続先として案内している。既存の解析基盤をエージェントから利用する用途の広がりは背景として考えられるが、REAからの流入や個別更新との因果は確認できない。[公式配布ページ](https://github.com/NationalSecurityAgency/ghidra/releases/tag/Ghidra_12.1.4_build)、[REA README](https://raw.githubusercontent.com/morluto/rea/HEAD/README.md)

### 7. debpalash/VoiceStudio

- **リンク**：[https://github.com/debpalash/VoiceStudio](https://github.com/debpalash/VoiceStudio)
- **概要・目的**：音声クローン、音声設計、吹き替え、文字起こし、音声入力、オーディオブック制作をまとめた音声処理アプリケーション。
- **主な特徴**：Electronアプリ、ローカルモデル管理、GPU・CPU処理、ローカルAPI・MCPを備える。646言語への対応を掲げるが、機能と品質は選ぶエンジン・モデルによる。アプリ本体はAGPL-3.0、モデルや音声の権利は別。[README](https://raw.githubusercontent.com/debpalash/VoiceStudio/HEAD/README.md)
- **想定用途・対象者**：許可を得た音声を使う吹き替え・ナレーション担当者、ローカル音声処理を業務へ組み込みたい開発者。
- **その他特筆事項**：Electronへの移行に伴い旧Tauri版とは導入経路が異なる。必要なGPUメモリー・保存容量はモデルごとに異なり、音声クローンには本人の許可が必要。総スター80,387（今週+15,125）。
- **トレンド入りの理由**：公式0.5.6の公開情報では、参照音声の差し替え、長い参照クリップ、長編オーディオブック、Windowsバックエンド、MCPなどの改善を確認できる。現行READMEもローカル制作とエージェント連携を同じアプリで扱う構成を示す。制作工程をまとめて手元で進めたい需要は注目背景と考えられるが、9月の公開を今週の直接要因とはしない。[公式リリース](https://github.com/debpalash/VoiceStudio/releases/tag/v0.5.6)

### 8. mksglu/context-mode

- **リンク**：[https://github.com/mksglu/context-mode](https://github.com/mksglu/context-mode)
- **概要・目的**：大量のツール出力をそのまま会話に入れず、必要な情報を検索・抽出してエージェントへ渡すMCPサーバー。コンテキスト圧縮後の作業継続も扱う。
- **主な特徴**：コード実行、ファイル処理、取得・索引化、FTS5とBM25による検索、SQLiteへのイベント記録を組み合わせる。各開発ツール用の接続方法を持つ。Elastic License 2.0によるソース公開で、利用条件はMIT等と異なる。[README](https://raw.githubusercontent.com/mksglu/context-mode/HEAD/README.md)
- **想定用途・対象者**：ログ、検索結果、コード、ブラウザー情報を大量に扱う開発者・調査担当者。情報量を減らしても必要な根拠を取り出せるか評価したい人。
- **その他特筆事項**：READMEの削減率は作者の測定例であり、実際の削減率・回答精度を保証しない。コード実行ツールは実行プロセスのファイル権限を引き継ぎ、完全なOS隔離機能ではない。総スター31,651（今週+2,968）。
- **トレンド入りの理由**：公式リリースには、実際のターン単位の使用量・費用を記録する機能と、コンテキスト削減・費用計測の修正がある。大量出力を短くするだけでなく、効果を計測して運用する点が関心の背景と考えられる。これらは6月の既存機能で、今週固有の新規公開や拡散の起点は確認できていない。[公式リリース本文](https://github.com/mksglu/context-mode/releases)

### 9. heygen-com/hyperframes

- **リンク**：[https://github.com/heygen-com/hyperframes](https://github.com/heygen-com/hyperframes)
- **概要・目的**：HTML・CSS・メディア・アニメーションからMP4動画を生成する、AIエージェント向けの制作フレームワーク。
- **主な特徴**：CLIによる検査・プレビュー・レンダリング、素材の準備、ブランド設定、編集可能な部品集を備える。現行READMEは4つの基本スキルと、Figma・スライド・移行用の任意スキルを案内する。Apache-2.0。[README](https://raw.githubusercontent.com/heygen-com/hyperframes/HEAD/README.md)
- **想定用途・対象者**：製品紹介、操作説明、更新紹介、図表を使う動画を、Web技術とエージェントで制作する開発者・制作担当者。
- **その他特筆事項**：ローカルCLIはNode.js 22以降とFFmpegを必要とする。素材の利用条件、音声品質、文字の表示、最終動画の再現性は作品ごとに確認する。総スター69,201（今週+5,740）。
- **トレンド入りの理由**：現行READMEでは、企画から素材準備・検査・プレビュー・書き出しまでの手順と、必要なスキルだけを追加する導入方法を公開している。制作の各工程をエージェントへ渡せる点は継続的な注目材料。直近の単独告知を今週の増加と結び付ける証拠は確認できていない。[公式の制作・導入説明](https://github.com/heygen-com/hyperframes#skills)

### 10. cursor/plugins

- **リンク**：[https://github.com/cursor/plugins](https://github.com/cursor/plugins)
- **概要・目的**：Cursor向けに開発ツール、フレームワーク、業務サービスとの連携をプラグインとしてまとめる公式リポジトリ。
- **主な特徴**：コードレビュー、学習、プラグイン作成、並列作業に加え、Google Workspace、GitHub、CRMなどの連携を掲載する。各ディレクトリにmanifestを持ち、提供機能・認証・利用条件はプラグインごとに異なる。[README](https://raw.githubusercontent.com/cursor/plugins/HEAD/README.md)
- **想定用途・対象者**：開発環境からレビュー・調査・業務情報へのアクセスをまとめたいCursor利用者や、チームの導入候補を整理する管理者。
- **その他特筆事項**：外部サービス連携では参照だけでなく更新操作を含むものもある。実際に必要な権限と接続先、ライセンスを個別に確認する。総スター13,396（今週+2,049）。
- **トレンド入りの理由**：公式READMEには、分担作業のorchestrate、レビューのthermos、ドキュメント表示や学習、業務サービス連携など、開発の前後を含む具体的な用途が並ぶ。拡張の配布単位をプラグインへまとめる動きが注目背景と考えられる。10月のフォーラム投稿だけを公式機能追加の根拠にはせず、今週の直接要因は未特定。[公式プラグイン一覧](https://github.com/cursor/plugins#plugins)

### 11. HKUDS/CLI-Anything

- **リンク**：[https://github.com/HKUDS/CLI-Anything](https://github.com/HKUDS/CLI-Anything)
- **概要・目的**：既存ソフトウェアをエージェントが操作しやすいCLIで包み、生成・導入・利用するための手順とツール集。
- **主な特徴**：ソースを調べてCLIを構築する手順、JSON出力、REPL、テストを案内し、CLI-Hubで対応ツールを検索・導入できる。既存の生成済みCLIを使う経路もある。Apache-2.0。[README](https://raw.githubusercontent.com/HKUDS/CLI-Anything/HEAD/README.md)
- **想定用途・対象者**：GUI中心の既存ツールや業務ソフトの処理を、コマンド経由で自動化・再利用したい開発者。
- **その他特筆事項**：任意のソフトを無条件で操作できるわけではなく、対象ソフト、生成したCLI、権限、依存関係ごとの確認が必要。既存アプリの利用条件も引き継ぐ。総スター55,927（今週+3,681）。
- **トレンド入りの理由**：6月25日公開と表示されるv0.4.0では、複数CLIの導入と機能充足をまとめて確認するCLI-Matrix、30件のCLI追加、既存ツールの修正を公開した。単独のコマンド生成から一連の作業へ対象を広げ、既存資産をエージェントへつなぐ需要に対応する点が、注目の背景として考えられる。ただし、6月のリリースを今週の出来事とはせず、再注目の直接要因は未確認。[公式リリース](https://github.com/HKUDS/CLI-Anything/releases/tag/v0.4.0)

### 12. akitaonrails/ai-memory

- **リンク**：[https://github.com/akitaonrails/ai-memory](https://github.com/akitaonrails/ai-memory)
- **概要・目的**：Claude Code、Codexなど異なるエージェント、端末、利用者の間で、作業中の判断・失敗・残課題を引き継ぐ長期記憶サーバー。
- **主な特徴**：Git管理のMarkdownを原本にし、検索用索引を派生させる。フックによる記録、検索、所有者を持つ引き継ぎ、任意のLLMによる整理を備える。基本の記録・検索・引き継ぎはLLM呼び出しなしで動作する設計。MIT。[README](https://raw.githubusercontent.com/akitaonrails/ai-memory/HEAD/README.md)
- **想定用途・対象者**：複数のエージェントや端末を使い分け、同じ説明や調査を繰り返す負担を減らしたい開発者・チーム。
- **その他特筆事項**：ネイティブWindowsは実験的で、WSL2はサポート対象。共有サーバーではプロジェクト・個人の情報範囲、記録対象、削除・保持の扱いを確認する。総スター12,320（今週+2,833）。
- **トレンド入りの理由**：公式サイトの10月16日版3.1.0は、Windows導入、接続するエージェントの選択、管理された切り替え時のローカル履歴引き継ぎ、管理画面の追加を説明する。記憶の保存に加えて製品をまたぐ作業継続を整備した点は、今週の注目材料。スター増加との因果関係は独立には確認できない。[公式変更説明](https://aimemory.sh/download/)

### 13. anomalyco/opencode

- **リンク**：[https://github.com/anomalyco/opencode](https://github.com/anomalyco/opencode)
- **概要・目的**：ターミナルやデスクトップから開発作業を行う、ソース公開型のAIコーディングエージェント。
- **主な特徴**：開発を進めるbuild、既定で編集を禁止するplan、調査用のサブエージェントを備える。デスクトップ版はmacOS・Windows・Linux向けに提供する。[README](https://raw.githubusercontent.com/anomalyco/opencode/HEAD/README.md)
- **想定用途・対象者**：モデルやツールの接続を選びながら、調査・設計・実装を同じ実行環境で進めたい開発者。
- **その他特筆事項**：デスクトップ版はベータ。2.1ではSDK・HTTPメッセージ・プラグイン契約に意図的な変更があり、既存連携の更新が必要になる場合がある。総スター219,670（今週+6,545）。
- **トレンド入りの理由**：10月20日の2.1.0はWindowsの永続ターミナル、TUIのタスク一覧、長時間コマンドの接続改善を発表。21日の2.1.2では利用上限後の復帰や導入時の問題も改善した。長時間・複数工程の作業を継続するための変更が、利用候補としての関心を支えると考えられる。個別変更が掲載を引き起こしたとまでは断定できない。[公式変更履歴](https://opencode.ai/changelog)

### 14. wshobson/agents

- **リンク**：[https://github.com/wshobson/agents](https://github.com/wshobson/agents)
- **概要・目的**：専門エージェント、スキル、コマンドを作業分野別のプラグインとして配布し、複数のAI開発ツールで再利用するライブラリー。
- **主な特徴**：現行READMEは94プラグイン、ローカルの202エージェント・185スキル・105コマンドを案内する。Python・JavaScript、レビュー、テスト、基盤、セキュリティなどを扱い、Markdown原本から製品別の形式へ適応する。リポジトリはMIT、外部プラグインの条件は別。[README](https://raw.githubusercontent.com/wshobson/agents/HEAD/README.md)
- **想定用途・対象者**：チーム内の開発手順を再利用したい人、特定分野だけの専門知識をエージェントへ追加したい開発者。
- **その他特筆事項**：同じ原本でも、Codexの標準導入と生成アダプターでは公開される部品が異なる。全件の一括導入より、必要な分野と利用環境に合う経路を選ぶ。総スター41,474（今週+785）。
- **トレンド入りの理由**：公式READMEは、Claude CodeだけでなくCodex・Cursor・OpenCode・Copilotなどへの導入経路と機能差を具体的に示している。専門家の手順を共有しながら実行製品を選べる点が、スキル配布への関心の背景と考えられる。新たな対応が今週公開されたかは確認できず、製品横断対応を今週の新機能とは断定しない。[公式の対応表](https://github.com/wshobson/agents#multi-harness-support)

### 15. earthtojake/text-to-cad

- **リンク**：[https://github.com/earthtojake/text-to-cad](https://github.com/earthtojake/text-to-cad)
- **概要・目的**：エージェントが3Dモデル、図面、製造用データを作成・表示・確認するためのプラグインとスキル集。
- **主な特徴**：STEP・GLB・STL・3MFの生成、製造性の確認、図面、DXF、ロボット記述などを扱う。build123d・Open CASCADEとローカルビューアーを組み合わせる。MIT。[README](https://raw.githubusercontent.com/earthtojake/text-to-cad/HEAD/README.md)
- **想定用途・対象者**：部品の試作、形状の比較、寸法付き図面、ロボットの構造データをエージェントと作りたい設計者・開発者。
- **その他特筆事項**：開発用mainと配布用latest、プラグインと単独スキルの導入を区別する。モデルの生成成功だけで寸法・製造性の確認は完了しない。総スター22,275（今週+2,000）。
- **トレンド入りの理由**：10月20日公開と表示される0.7.25ではPencil・Shapes、要素単位のMeasure、選択メニューなど、形状を調整・確認する操作を追加。同日の0.7.26はNodeがPATHにない環境でのメッシュ出力などを修正した。生成後の確認・修正を進めやすくする更新は注目材料だが、週間増加との因果は未確認。[機能追加の公式リリース](https://github.com/earthtojake/text-to-cad/releases/tag/v0.7.25)、[公式リリース一覧](https://github.com/earthtojake/text-to-cad/releases)

### 16. stablyai/orca

- **リンク**：[https://github.com/stablyai/orca](https://github.com/stablyai/orca)
- **概要・目的**：複数のCLIエージェントをGit worktreeごとに分け、実行・比較・レビューするデスクトップ作業環境。
- **主な特徴**：並列worktree、分割ターミナル、内蔵ブラウザー、差分へのコメント、GitHub・Linear、SSH作業、モバイルからの監視・指示をまとめる。Claude Code・CodexなどのCLIに対応する。MIT。[README](https://raw.githubusercontent.com/stablyai/orca/HEAD/README.md)
- **想定用途・対象者**：複数の実装案や作業をエージェントへ並行して任せ、差分を見て採用する開発者・レビュー担当者。
- **その他特筆事項**：作業場所の分離は変更の品質を保証しない。採用する差分、競合、テスト、SSH・モバイル接続先の権限は利用者が確認する。総スター101,224（今週+8,705）。
- **トレンド入りの理由**：10月21日公開と表示される1.4.237は、スマートフォンからのノート編集、ヘッドレス環境のMarkdown保存、会話の再開・巻き戻し、リモート環境の改善を説明する。複数エージェントを動かした後の監視・再開・レビューまで扱う拡張が注目材料。同リリースは10万スター到達にも言及するが、その節目自体を品質や増加原因の証拠にはしない。[公式リリース本文](https://github.com/stablyai/orca/releases/tag/v1.4.237)

レビュー対象16件／サマリー完成16件。
