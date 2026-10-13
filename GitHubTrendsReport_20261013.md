---
layout: default
title: "GitHubトレンドリポジトリ レビュー(週間: 2026年10月13日時点)"
---

# GitHubトレンド週間レビュー（2026年10月13日時点）

## 全体トレンドの概観

取得時点の週間トレンドでは、AIエージェントを使う開発と制作の道具が中心。11件のうち8件が、テスト、動画、CAD、解析、スキル配布、記憶管理、複数エージェント運用に関わる。単体のモデルより、仕事を実行して成果を確認する工程へ関心が広がっている。

e2eは自然言語の操作とアサーションを組み合わせ、hyperframesとtext-to-cadは動画や3Dモデルを出力する。skills、claude-mem、plugins、openrigは、その作業を繰り返すための手順と環境を整える。一方、AnyPS5の互換性開発、Flutterの複数環境向けアプリ開発、openGymの自己ホスト型サービスも掲載された。

対象は2026年10月13日JSTに取得した[GitHub Trending週間表示](https://github.com/trending?since=weekly)の全11件。順序とスター数は取得画面に従う。トレンド理由にはWeb検索で確認した公式告知・更新と、注目背景の解釈を記す。更新が掲載を引き起こしたという因果関係を独立に検証したものではない。

## リポジトリ別サマリー

### 1. boykopovar/AnyPS5

- **リンク**：[https://github.com/boykopovar/AnyPS5](https://github.com/boykopovar/AnyPS5)
- **概要・目的**：PS5の実行ファイルをLinux・Windowsのネイティブ形式へ変換する互換性開発ツール。ゲーム実行環境の移植と研究を目的とする。
- **主な特徴**：リリンカーで実行形式を変換し、システムprxライブラリを独自実装。シェーダーをSPIR-Vへ変換する。C++製、GPL-2.0。 [README](https://github.com/boykopovar/AnyPS5/blob/main/README.md)
- **想定用途・対象者**：ゲーム互換レイヤー、実行形式、保存技術を研究する開発者。
- **その他特筆事項**：未対応の状態では例外終了する。タイトルごとの動作状況は公開の進捗表で確認する。 総スター33,150（今週+27,263）。
- **トレンド入りの理由**：9月29日JST公開のv0.1.1で、フォント、セーブデータ、メディア再生などを追加。実際に動かせる機能が増え、PS5実行ファイルをPCへ移植する方式が注目材料になっている。 [公式出典](https://github.com/boykopovar/AnyPS5/releases/tag/v0.1.1)

### 2. tester-army/e2e

- **リンク**：[https://github.com/tester-army/e2e](https://github.com/tester-army/e2e)
- **概要・目的**：自然言語によるエージェント操作と、通常のアサーションを同じテストで使うWeb・iOS・Android向けE2Eテスト基盤。
- **主な特徴**：TypeScript製。WebはPlaywright、モバイルはagent-deviceを利用。検証済みの操作をキャッシュし、変更がない次回実行ではモデル呼び出しなしで再生する。Apache-2.0。 [README](https://github.com/tester-army/e2e/blob/main/README.md)
- **想定用途・対象者**：Webとモバイルの業務フローを検証する開発者・QA担当者。
- **その他特筆事項**：1.0未満でAPIと設定は変更される可能性がある。エージェント操作の結果をロケーターとアサーションで検証できる。 総スター9,670（今週+5,582）。
- **トレンド入りの理由**：TesterArmyが10月1日にOSS化を公式発表。Web・iOS・Androidで共通APIを使い、操作再生で毎回のモデル利用を減らす設計を公開した。AIテストの実行費用と既存テストとの共存に具体策を出したことが注目の背景。 [公式出典](https://tester.army/blog/introducing-e2e)

### 3. mattpocock/skills

- **リンク**：[https://github.com/mattpocock/skills](https://github.com/mattpocock/skills)
- **概要・目的**：Matt Pocockが日常の開発に使うエージェント向けスキル集。要件確認から実装、レビューまでの工程を再利用する。
- **主な特徴**：小さく変更・組み合わせられる手順を配布。Claude Code、Codex、Copilotなどに対応。課題管理方法や共有用語をプロジェクトごとに設定できる。 [README](https://github.com/mattpocock/skills/blob/main/README.md)
- **想定用途・対象者**：AIに任せる工程を調整しながら実際のアプリを開発するエンジニア。
- **その他特筆事項**：完成アプリではなく、エージェントの作業手順を配布するリポジトリ。導入時に必要なスキルを選ぶ。 総スター288,214（今週+11,139）。
- **トレンド入りの理由**：10月4日のv1.3.1でimplement-specを正式な開発スキルへ追加。仕様をタスクグラフとして読み、独立したworktreeで並列実装し、1つの統合ブランチへまとめてレビューする手順を整えた。AI開発の再現性を高める具体的な工程が注目材料。 [公式出典](https://github.com/mattpocock/skills/releases/tag/v1.3.1)

### 4. heygen-com/hyperframes

- **リンク**：[https://github.com/heygen-com/hyperframes](https://github.com/heygen-com/hyperframes)
- **概要・目的**：HTML・CSS・素材・時間位置を指定できるアニメーションからMP4を生成するHeyGenの動画制作フレームワーク。
- **主な特徴**：ローカルCLIとAIエージェント向けスキルを提供。構成の計画、HTML作成、プレビュー、レンダリングまでを扱う。TypeScript製、Apache-2.0。 [README](https://github.com/heygen-com/hyperframes/blob/main/README.md)
- **想定用途・対象者**：説明動画や製品紹介動画をコードとエージェントで制作する開発者・制作担当者。
- **その他特筆事項**：公式のHyperFrames StudioはmacOS・Linux版を提供し、Windows版は提供予定と案内。動画素材と音声を含む制作工程を扱う。 総スター61,948（今週+4,482）。
- **トレンド入りの理由**：公式サイトがエージェント向け動画エディターHyperFrames Studioを公開し、動画制作の操作環境まで提供している。10月12日のv0.8.150ではレンダリング時のメモリ対策と合成全体への音声効果を追加。制作から書き出しまで使える範囲の拡大が注目材料。 [公式出典](https://www.hyperframes.dev/)、[関連出典](https://github.com/heygen-com/hyperframes/releases/tag/v0.8.150)

### 5. thedotmack/claude-mem

- **リンク**：[https://github.com/thedotmack/claude-mem](https://github.com/thedotmack/claude-mem)
- **概要・目的**：エージェントの作業を記録・要約し、関連情報を後続セッションへ渡す永続的な記憶管理システム。
- **主な特徴**：ツール利用の観測、意味的な要約、次回セッションへの文脈注入を組み合わせる。複数のエージェント環境に対応。TypeScript製、Apache-2.0。 [README](https://github.com/thedotmack/claude-mem/blob/main/README.md)
- **想定用途・対象者**：長い開発を複数セッションで進め、判断や作業履歴を引き継ぎたい開発者。
- **その他特筆事項**：利用方式によってローカル処理とホスト型の扱いが異なる。server runtimeと既定のworker runtimeの区別が必要。 総スター100,156（今週+3,762）。
- **トレンド入りの理由**：10月13日JSTのv13.36.1で、server runtimeのprivate指定情報を送信前に除去する修正と、データベース更新時の競合対策を公開。セッションをまたぐ記憶を実運用するための情報保護と整合性の改善が続いている。既定のworker runtimeはprivate送信問題の影響外と公式に説明。 [公式出典](https://github.com/thedotmack/claude-mem/releases/tag/v13.36.1)

### 6. flutter/flutter

- **リンク**：[https://github.com/flutter/flutter](https://github.com/flutter/flutter)
- **概要・目的**：Dartでモバイル・Web・デスクトップ向けアプリを開発するUIフレームワーク。共通のコードで複数環境へ展開する。
- **主な特徴**：ウィジェット、ホットリロード、パッケージ群、FFIやプラットフォームAPIによるネイティブ連携を提供。 [README](https://github.com/flutter/flutter/blob/master/README.md)
- **想定用途・対象者**：複数プラットフォームのアプリを開発するチームとDart開発者。
- **その他特筆事項**：AIエージェント用プラグインそのものではなく、利用者向けアプリを実装する基盤。GitHubのlatest release APIだけで現行SDKの最新版を判断しない。 総スター179,996（今週+806）。
- **トレンド入りの理由**：Flutter公式ブログが10月8日にGenkit Dart 1.0を発表。Dart・Flutterで本番向けAI機能とエージェントの処理フローを作る選択肢を増やした。今回の週間一覧でAI開発関連が多いことと合わせ、既存のアプリ基盤へのAI機能統合が注目の背景と考えられる。 [公式出典](https://flutter.dev/blog/announcing-genkit-dart-1-0)

### 7. cursor/plugins

- **リンク**：[https://github.com/cursor/plugins](https://github.com/cursor/plugins)
- **概要・目的**：Cursorのプラグイン仕様と公式プラグイン集。開発ツール、フレームワーク、外部サービスとの連携を配布する。
- **主な特徴**：独立したディレクトリと.cursor-plugin/plugin.jsonで各プラグインを管理。MCP、スキル、サブエージェント、ルール、hooksをまとめられる。 [README](https://github.com/cursor/plugins/blob/main/README.md)
- **想定用途・対象者**：Cursorの作業手順を拡張する開発者と、共通の拡張を配布するチーム。
- **その他特筆事項**：READMEにはレビュー、学習、並列エージェント運用、Google Workspaceなどの連携例を掲載。 総スター11,095（今週+1,144）。
- **トレンド入りの理由**：Cursorは公式発表でMCPやスキルをまとめるMarketplaceを開設し、Google Workspace連携も公式に追加した。外部ツールの操作と社内の作業手順を同じエージェントへ配布できる点が注目材料。今回の掲載に直接つながる新規発表は確認できず、背景として整理した。 [公式出典](https://prod.cursor.com/blog/marketplace)、[関連出典](https://cursor.com/changelog/google-workspace-plugins)

### 8. earthtojake/text-to-cad

- **リンク**：[https://github.com/earthtojake/text-to-cad](https://github.com/earthtojake/text-to-cad)
- **概要・目的**：エージェントからローカルで3Dモデルを生成し、設計と製造向け出力を進めるCADツール。
- **主な特徴**：STEP・GLB・STL・3MFの出力、製造向けチェック、図面生成、加工サービス連携を扱う。複数エージェント向けのプラグインとスキルを提供。Python製、MIT。 [README](https://github.com/earthtojake/text-to-cad/blob/main/README.md)
- **想定用途・対象者**：自然言語とコードで3Dモデルを作る設計者、試作担当者、開発者。
- **その他特筆事項**：開発用mainと配布用latestブランチを分ける。プラグインとスキルの重複導入を避ける案内がある。 総スター19,712（今週+2,441）。
- **トレンド入りの理由**：10月12日JSTのv0.7.21でSTEP処理のクラッシュ、初回スナップショットの競合、Windowsワーカー表示を修正。モデル生成だけでなく、確認と出力までを既存エージェントから実行できる機能が注目材料。直近更新は対応環境の安定化を進めた。 [公式出典](https://github.com/earthtojake/text-to-cad/releases/tag/v0.7.21)

### 9. mvschwarz/openrig

- **リンク**：[https://github.com/mvschwarz/openrig](https://github.com/mvschwarz/openrig)
- **概要・目的**：Claude Code、Codex、Piを、役割と担当作業を持つ継続的なエージェントチームとして運用する基盤。
- **主な特徴**：複数エージェントの共有文脈、担当、メッセージ、再開を管理。Node.jsとtmuxを使用。Apache-2.0。 [README](https://github.com/mvschwarz/openrig/blob/main/README.md)
- **想定用途・対象者**：複数モデルやエージェントで長期の開発作業を進めるチーム。
- **その他特筆事項**：WindowsはWSL2を利用。起動時にhooksや信頼設定を変更するため、変更内容を公式文書で説明している。 総スター7,290（今週+2,056）。
- **トレンド入りの理由**：10月12日のv0.6.10で、利用プロバイダーの選択、Claudeセッションの復元、Codexへの送信を改善。56変更のうち38件が外部貢献者10人の変更と公式に報告。複数エージェントを継続運用する機能と、実利用に基づく改善が注目の背景。 [公式出典](https://github.com/mvschwarz/openrig/releases/tag/v0.6.10)

### 10. morluto/rea

- **リンク**：[https://github.com/morluto/rea](https://github.com/morluto/rea)
- **概要・目的**：アプリの挙動やバイナリ、JavaScriptなどをエージェントから調査するリバースエンジニアリング基盤。
- **主な特徴**：MCPとCLIを提供。Hopper、Ghidra、IDAなどと連携し、根拠と限界を付けた解析結果を返す。TypeScript製、MIT。 [README](https://github.com/morluto/rea/blob/main/README.md)
- **想定用途・対象者**：ソースが手元にないアプリの仕組みを調査する開発者と解析担当者。
- **その他特筆事項**：解析対象ごとに必要なエンジンと実行環境が異なる。週間増加数はGitHub表示値で、増加経緯を独自検証したものではない。 総スター167,547（今週+130,471）。
- **トレンド入りの理由**：10月11日の6.4.0で、ADBによるAndroid端末・アプリ調査、JEB連携、大きな解析結果を段階的に読む機能を追加。エージェントから扱える対象をネイティブアプリやAndroidまで広げたことが注目材料。スター急増の具体的な拡散経路は確認できなかった。 [公式出典](https://github.com/morluto/rea/releases/tag/rea-agents-6.4.0)

### 11. DuarteSantos8/openGym

- **リンク**：[https://github.com/DuarteSantos8/openGym](https://github.com/DuarteSantos8/openGym)
- **概要・目的**：自分のサーバーでトレーニングと体重を記録するアプリ。運動記録を自分で管理することを目的とする。
- **主な特徴**：ルーティン計画、セット記録、疲労の可視化、既存アプリからの取り込み、パスキー認証、オフライン動作と端末間同期を提供。アプリ本体はAGPL-3.0。 [README](https://github.com/DuarteSantos8/openGym/blob/main/README.md)
- **想定用途・対象者**：筋力トレーニングを記録する利用者と、データの保存先を自分で管理したい利用者。
- **その他特筆事項**：運動の画像・アニメーションにはアプリ本体と異なる利用条件がある。自己ホスト環境で利用できる。 総スター10,626（今週+6,621）。
- **トレンド入りの理由**：公式ロードマップでは10月7日にUI刷新・ローテーション・同期改善、10月9日に運動カタログを1,324から5,632件へ拡大したと報告。自己ホスト型のまま記録と検索の使い勝手を高めた大型更新が、今週の注目材料になっている。 [公式出典](https://github.com/DuarteSantos8/openGym/blob/main/ROADMAP.md)

レビュー対象11件／サマリー完成11件。
