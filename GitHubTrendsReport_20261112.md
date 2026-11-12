---
layout: default
title: "GitHubトレンドリポジトリ レビュー(週間: 2026年11月12日時点)"
---

# GitHubトレンド週間レビュー（2026年11月12日時点）

## 全体トレンドの概観

AIに作業手順を教えるスキル集と、実際の画面を操作させる道具が目立つ。Anthropic、Google、Matt Pocockのスキル集は、文書作成、クラウド運用、開発工程の知識を再利用するためのもの。Vercelのagent-browserとagent-desktopは、それぞれWebページとネイティブアプリの操作を受け持つ。スキルに書いた指示を、観察できる画面と確認可能な操作へつなぐ構成が共通している。

業務データの扱いにも注目したい。NVIDIAのAuto Ontologyは、売上などの指標の意味やデータの関係を整理し、AIの問い合わせに根拠を渡す。ScraplingはWeb情報の収集、Cloudflareのsecurity-audit-skillはコードの調査と再検証を支援する。いずれも生成された答えを採用するまでの手順が重要になる。物理シミュレーターのMuJoCoも含まれ、AI関連の関心が画面操作から実世界の動作検証まで広がる顔ぶれとなった。ただし、掲載だけで各用途の普及や製品品質を判断することはできない。

## リポジトリ別サマリー

### 1. NVIDIA/auto-ontology

- **リンク**：[https://github.com/NVIDIA/auto-ontology](https://github.com/NVIDIA/auto-ontology)
- **概要・目的**：企業のデータベースにある項目、業務上の意味、指標の定義と関係を整理し、AIが自然言語の質問から適切なデータを参照するための基盤。
- **主な特徴**：メタデータから意味の辞書と関係図を組み立て、SQL生成、定義の照合、出典の提示を支援する。Web画面、MCP、CLI、APIから利用でき、Docker ComposeとKubernetes向け構成を備える。Apache-2.0。[README](https://github.com/NVIDIA/auto-ontology#readme)
- **想定用途・対象者**：部門ごとに売上や顧客の定義が異なる環境で、データ分析用AIを作る開発者、データ基盤担当者。問い合わせの前提をそろえる作業に向く。
- **その他特筆事項**：標準構成はNVIDIA NIMの推論サービスを利用する。接続するモデル、データベースの権限、認定済みの指標定義を用意する必要があり、導入だけで回答の正しさは保証されない。現時点では外部からの貢献を受け付けない旨も明記。総スター11,843（今週+7,947）。
- **トレンド入りの理由**：NVIDIAは11月6日更新の1.2.0コンテナを公開し、意味情報をエージェントへ提供するREST APIを説明している。業務指標の食い違いを扱えることと、試せる配布物があることは注目背景として考えられる。今週の増加を特定の告知に結び付ける直接要因は未確認。[公式配布情報](https://catalog.ngc.nvidia.com/orgs/nvidia/-/containers/auto-ontology/1.2.0)

### 2. anthropics/skills

- **リンク**：[https://github.com/anthropics/skills](https://github.com/anthropics/skills)
- **概要・目的**：AIに専門的な仕事の進め方を教えるスキルの公式サンプル集。文章による指示と、必要なスクリプトや参考資料を一つのフォルダにまとめる。
- **主な特徴**：SKILL.mdを中心に、文書作成、開発、デザインなどの手順を提供する。READMEは文書系を含むスキルのApache-2.0公開を説明しており、DOCXとPDFの個別ライセンス本文でも確認できた。[README](https://github.com/anthropics/skills#readme)、[DOCXのライセンス](https://github.com/anthropics/skills/blob/main/skills/docx/LICENSE.txt)、[PDFのライセンス](https://github.com/anthropics/skills/blob/main/skills/pdf/LICENSE.txt)
- **想定用途・対象者**：表計算や資料作成などの定型業務をAIに任せたい利用者、社内手順をスキルとして整備する開発者。
- **その他特筆事項**：公開サンプルの実行結果は環境や入力によって変わる。自社の書式や確認条件を加え、生成したファイルを実際のアプリで確認したい。仕様の管理団体と、このサンプル集の提供者は区別する。総スター193,146（今週+5,738）。
- **トレンド入りの理由**：Anthropicは10月22日、Agent Skills仕様をAgentic AI Foundationへ寄贈すると発表した。複数製品で同じ形式を扱えるようにする動きは、サンプル集を読む背景になる。ただし、仕様の寄贈と今週のスター増加の因果関係は未確認。[公式発表](https://www.anthropic.com/news/donating-agent-skills-to-the-agentic-ai-foundation)

### 3. vercel-labs/agent-desktop

- **リンク**：[https://github.com/vercel-labs/agent-desktop](https://github.com/vercel-labs/agent-desktop)
- **概要・目的**：AIからWindows、macOS、Linuxのデスクトップアプリを操作するためのCLIとライブラリ。操作を判断するAI自体は含まない。
- **主な特徴**：OSのアクセシビリティ情報からボタンや入力欄を読み取り、参照番号で操作する。スナップショットごとの参照により古い対象への操作を検出し、MCPやCライブラリ経由でも利用できる。Apache-2.0。[README](https://github.com/vercel-labs/agent-desktop#readme)
- **想定用途・対象者**：ブラウザ外の業務アプリ、OSのダイアログ、ネイティブ画面をAIで操作・確認する開発者やテスト担当者。
- **その他特筆事項**：アクセシビリティ情報を公開しないアプリでは対象を認識できない場合がある。実行した操作の成功は、変更後の画面や保存結果で確かめる必要がある。総スター22,090（今週+7,772）。
- **トレンド入りの理由**：11月5日のv1.2.0ではMCPサーバーを追加した。既存のMCP対応AIから接続しやすくなった点は、導入を試すきっかけとして考えられる。VercelもWebとネイティブ画面の使い分けを公式に説明しているが、掲載の直接要因は未確認。[リリース](https://github.com/vercel-labs/agent-desktop/releases/tag/v1.2.0)、[公式解説](https://vercel.com/i/browser-vs-desktop-automation)

### 4. milind-soni/OpenMausBot

- **リンク**：[https://github.com/milind-soni/OpenMausBot](https://github.com/milind-soni/OpenMausBot)
- **概要・目的**：複数のAIエージェントを、チャットアプリの連絡先のように扱うアプリ。ボットごとにモデルや作業環境、連携先を設定する。
- **主な特徴**：ローカルのClaude、CodexなどのCLIを利用し、会話履歴をローカルに保存する。ボットへの依頼、承認、アプリ連携、クラウド環境やローカルVMでの作業をまとめる。基本部分はApache-2.0だが、enterpriseディレクトリには別ライセンスがある。[README](https://github.com/milind-soni/OpenMausBot#readme)
- **想定用途・対象者**：調査、開発、事務処理などの担当AIを分け、一つのチャット画面から依頼と進捗を管理したい利用者。
- **その他特筆事項**：ローカル保存でもモデルや連携サービスへの送信は発生する。端末版とCLI版では認証情報の保存方法が異なり、ホストPC操作の対応範囲もOSによって違う。総スター21,240（今週+9,257）。
- **トレンド入りの理由**：11月11日の0.1.153で、大きな依頼の分割内容を提示し、並列実行した結果をまとめるBurst modeを発表した。複数AIへの依頼をチャットで扱える使い方は関心の背景として考えられるが、機能追加がスター増加を引き起こしたかは未確認。[公式リリース](https://github.com/milind-soni/OpenMausBot/releases/tag/v0.1.153)

### 5. vercel-labs/agent-browser

- **リンク**：[https://github.com/vercel-labs/agent-browser](https://github.com/vercel-labs/agent-browser)
- **概要・目的**：AIがWebページを観察し、ボタン操作やフォーム入力を行うためのブラウザ自動化CLI。
- **主な特徴**：アクセシビリティ情報のスナップショットと参照番号を用いた操作、スクリーンショット、状態の比較、セッション管理、MCP接続を提供する。Rust製CLIとバックグラウンドのブラウザ接続を組み合わせる。Apache-2.0。[README](https://github.com/vercel-labs/agent-browser#readme)
- **想定用途・対象者**：Webアプリの動作確認、表示不具合の再現、フォーム入力、資料として残す画面の取得をAIに支援させたい開発者とテスト担当者。
- **その他特筆事項**：画面が変わった後は再観察して対象を取り直す。操作コマンドの成功に加えて、入力値や遷移先、保存された成果物を確認する。総スター49,878（今週+4,183）。
- **トレンド入りの理由**：公式リリースではVercel Sandbox内のMCP接続支援や、保存したブラウザ状態の復元に関する修正を確認できる。画面操作を継続的なAIの作業へ組み込む整備が進んでいる。導入のしやすさは注目背景と考えられる一方、特定の更新と掲載の因果は未確認。[リリース情報](https://github.com/vercel-labs/agent-browser/releases)、[用途の公式解説](https://vercel.com/i/browser-vs-desktop-automation)

### 6. cloudflare/security-audit-skill

- **リンク**：[https://github.com/cloudflare/security-audit-skill](https://github.com/cloudflare/security-audit-skill)
- **概要・目的**：コードのセキュリティ監査をAIで進めるための手順と補助ツール。調査対象を整理し、候補を再検証して報告する。
- **主な特徴**：現行READMEは、事前調査、調査範囲に基づく探索、新しい検証者による確認、記録整理、記録の独立検証、報告の6段階を説明する。confirmed、needs_validation、rejectedを分け、調査範囲の台帳も管理する。MIT。[README](https://github.com/cloudflare/security-audit-skill#readme)
- **想定用途・対象者**：自社コードのレビュー、脆弱性候補の整理、再現証拠の確認を行うセキュリティ担当者や開発者。
- **その他特筆事項**：対象コードを実行する検証にはOS側の隔離や通信・書き込みの制限が必要。条件を満たせない候補は未検証として残す。スキル単体とCloudflare社内の大規模実行基盤は別のもの。総スター70,379（今週+11,507）。
- **トレンド入りの理由**：Cloudflareは6月18日の公式記事で、実際の監査基盤を作る出発点として初期スキルを公開したと説明している。調査範囲と再検証まで含めた手順を参照できることは継続的な注目の背景と考えられる。今週固有の拡散要因は未確認で、過去の公開を今週の新発表とは扱わない。[公式解説](https://blog.cloudflare.com/build-your-own-vulnerability-harness)

### 7. mattpocock/skills

- **リンク**：[https://github.com/mattpocock/skills](https://github.com/mattpocock/skills)
- **概要・目的**：要件の確認、仕様化、実装、テスト、レビューをAIと進めるための、小さく組み合わせ可能な開発スキル集。
- **主な特徴**：質問による前提整理、共通用語の記録、TDD、原因調査、設計確認などを提供する。複数のAI開発環境への導入経路があり、課題管理先や文書配置を初期設定する。MIT。[README](https://github.com/mattpocock/skills#readme)、[ライセンス](https://github.com/mattpocock/skills/blob/main/LICENSE)
- **想定用途・対象者**：AIが意図と違う実装をする、修正のたびに設計が複雑になる、確認せず完了を宣言するといった問題を減らしたい開発者。
- **その他特筆事項**：対話を増やす手順は小さな変更には重い場合がある。必要なスキルを選び、既存の用語、課題管理、承認条件と合わせる。総スター322,043（今週+9,575）。
- **トレンド入りの理由**：作者の公式ガイドでは、課題の保存先、状態ラベル、設計文書の配置を一度設定し、共通のスキルから参照する方式を具体化している。自分の開発環境へ適用しやすい点は注目背景として考えられる。今週固有の公開・拡散の直接要因は確認できなかった。[作者の導入解説](https://www.aihero.dev/skills-setup-matt-pocock-skills)

### 8. D4Vinci/Scrapling

- **リンク**：[https://github.com/D4Vinci/Scrapling](https://github.com/D4Vinci/Scrapling)
- **概要・目的**：PythonでWeb情報の取得、HTML解析、継続的な巡回を行うフレームワーク。単発のページ取得から複数ページの収集まで扱う。
- **主な特徴**：HTTP取得とブラウザ取得、CSS・XPathによる抽出、ページ構造の変化に対応する要素追跡、並列巡回、中断・再開、データ書き出しを提供する。AI向けMCP機能も用意。BSD-3-Clause。[README](https://github.com/D4Vinci/Scrapling#readme)
- **想定用途・対象者**：公開情報の調査、比較表の素材収集、Webデータの定期取得、検索用データの整形を行う開発者と調査担当者。
- **その他特筆事項**：対象サイトの利用条件と取得範囲に合わせて使う。動的な画面にはブラウザの導入が必要で、遠隔ブラウザ接続は0.5.1で移行が必要になる変更を含む。総スター101,650（今週+5,814）。
- **トレンド入りの理由**：11月4日の0.5.1では、短い動画による動きの観察、押したまま位置を調整するドラッグ操作、専用の遠隔ブラウザセッションを追加した。情報収集に加えてAIによる動的な画面操作を扱う拡張は注目背景と考えられる。掲載の直接要因は未確認。[公式リリース](https://github.com/D4Vinci/Scrapling/releases/tag/v0.5.1)

### 9. zed-industries/zed

- **リンク**：[https://github.com/zed-industries/zed](https://github.com/zed-industries/zed)
- **概要・目的**：高速な編集、共同作業、AIとの開発を一つの環境で扱うコードエディター。
- **主な特徴**：AtomとTree-sitterの開発者らによるエディターで、Windows、macOS、Linuxに対応する。複数のAIスレッドをプロジェクト単位で管理し、必要に応じてworktreeを分けられる。主要部分はGPL-3.0で、一部部品にはApache-2.0などが適用される。[README](https://github.com/zed-industries/zed#readme)、[並列エージェントの公式説明](https://zed.dev/blog/parallel-agents)
- **想定用途・対象者**：コードを読みながらAIの修正を比較したい開発者、複数案件や複数AIの作業を編集画面から管理したいチーム。
- **その他特筆事項**：利用するAIモデルの契約や送信条件は別途確認する。複数スレッドを動かす場合も、対象ファイルの範囲と採用する差分を確認する必要がある。総スター94,715（今週+2,310）。
- **トレンド入りの理由**：4月22日の公式記事では、同じウィンドウで複数エージェントを動かし、スレッドごとにモデルやアクセス先を選ぶ機能を発表している。AIの作業を人が編集・確認する環境への関心は背景として考えられるが、この過去の発表を今週の増加原因とは断定できない。[公式発表](https://zed.dev/blog/parallel-agents)

### 10. Donchitos/Claude-Code-Game-Studios

- **リンク**：[https://github.com/Donchitos/Claude-Code-Game-Studios](https://github.com/Donchitos/Claude-Code-Game-Studios)
- **概要・目的**：作りたいゲームの質問から企画、試作、確認、段階的な改良までをClaude Codeで進めるテンプレート。
- **主な特徴**：短い質問から1ページの企画を作り、遊べるブラウザゲームを生成する。画面や操作の自動確認、企画との照合、調整用パネル、機能単位の継続開発を支援する。Godot、Unity、Unreal向けの経路も用意。MIT。[README](https://github.com/Donchitos/Claude-Code-Game-Studios#readme)
- **想定用途・対象者**：個人ゲーム開発者、ゲームの案を短い試作で検討したい人。企画と動作確認をつなぐ開発工程の学習にも使える。
- **その他特筆事項**：作者はブラウザ経路の限られた試験例を示す一方、エンジン経路の同等な評価は未実施と説明する。自動操作の確認後も人が遊んで評価する工程を残している。総スター38,477（今週+3,150）。
- **トレンド入りの理由**：11月9日のv1.3.0は、質問、短い企画、ブラウザ試作、確認と修正を入口に据えた。最初に遊べる状態へ到達する道筋を具体化した点は注目背景として考えられる。更新とスター増加の因果関係は未確認。[公式リリース](https://github.com/Donchitos/Claude-Code-Game-Studios/releases/tag/v1.3.0)

### 11. google/skills

- **リンク**：[https://github.com/google/skills](https://github.com/google/skills)
- **概要・目的**：Google製品と技術をAIで扱うための公式スキル集。クラウド構築、運用、データ分析、広告関連の作業手順を提供する。
- **主な特徴**：Google Cloudの認証、GKE、BigQuery、Firebaseなどの手順に加え、複数製品を組み合わせた構成例を収録する。スキルの選択導入と更新、スキルとMCPをまとめたプラグインも扱う。Apache-2.0。[README](https://github.com/google/skills#readme)
- **想定用途・対象者**：Google Cloudを使う開発者、運用担当者、構成案や障害調査の手順をAIと検討したいチーム。
- **その他特筆事項**：公式の手順でも、対象アカウントの権限、課金、リージョン、既存構成に合わせた確認が必要。学習サービスのGoogle Skillsとは区別する。総スター23,943（今週+2,013）。
- **トレンド入りの理由**：Googleは4月22日のCloud Nextで公式Agent Skillsリポジトリを発表し、Google製品を扱うための知識を必要なときに読み込む仕組みを説明した。製品別の実務手順をまとめて参照できる点は注目背景と考えられる。今週の新規公開を意味するものではなく、今週固有の直接要因は未確認。[公式公開記事](https://cloud.google.com/blog/topics/developers-practitioners/level-up-your-agents-announcing-googles-official-skills-repository)

### 12. google-deepmind/mujoco

- **リンク**：[https://github.com/google-deepmind/mujoco](https://github.com/google-deepmind/mujoco)
- **概要・目的**：ロボットの関節や接触、身体の動作などを計算機上で試す物理エンジン。ロボット制御、強化学習、バイオメカニクスなどの研究開発に使う。
- **主な特徴**：C API、Pythonバインディング、Unity連携、対話的な可視化を提供する。ブラウザのビューアーや学習用ノートブックから動きを確認できる。ソースコードはApache-2.0、文書・画像・動画はCC BY 4.0。[README](https://github.com/google-deepmind/mujoco#readme)
- **想定用途・対象者**：ロボットの動作や接触を繰り返し評価する研究者と開発者。一般的な業務アプリの自動化とは必要知識が異なる。
- **その他特筆事項**：シミュレーションの結果を実機へ適用するには、質量、摩擦、センサーなどのモデル条件を合わせる必要がある。開発中のmainと安定した配布版も区別する。総スター17,645（今週+1,535）。
- **トレンド入りの理由**：11月11日の4.0.1では、MuJoCo StudioのWebビューアーをWindowsで使えるようにし、4.0.0で入った数値計算上の不具合も修正した。動きを確認できる環境の拡大と計算の修正は、導入・評価を進める背景として考えられる。今週の増加をこの更新に結び付ける根拠は未確認。[公式変更履歴](https://mujoco.readthedocs.io/en/stable/changelog.html#version-4-0-1-november-11-2026)

### 13. herdrdev/herdr

- **リンク**：[https://github.com/herdrdev/herdr](https://github.com/herdrdev/herdr)
- **概要・目的**：複数のAI開発ツールが動くターミナルをまとめ、実行中、応答待ち、待機中の状態を見ながら作業するための環境。
- **主な特徴**：画面分割、ローカルとSSH先の管理、切断後も動くバックグラウンドサーバー、対応エージェントのセッション復元を備える。CLIとソケットAPIでAIから操作でき、Rust製の単一バイナリとして配布する。Apache-2.0。[README](https://github.com/herdrdev/herdr#readme)
- **想定用途・対象者**：複数のAIに開発や調査を依頼し、応答を待って止まった作業を見落としたくない開発者。端末を閉じても長い処理を続けたい場合にも向く。
- **その他特筆事項**：クライアントを切り離す場合は実行を継続できるが、サーバーやPCの再起動後に元のプロセスが生き残るわけではない。保存レイアウトの復元と、対応AIの会話再開を分けて扱う。総スター50,340（今週+2,213）。
- **トレンド入りの理由**：公式文書は、接続を切っても実行する仕組みと、サーバー停止後の復元条件を具体的に説明している。複数AIを継続運用する際の管理負担を減らす用途は注目背景として考えられる。今週固有の発表や拡散の直接要因は確認できなかった。[公式の復元仕様](https://herdr.dev/tui/docs/session-state/)

レビュー対象13件／サマリー完成13件。
