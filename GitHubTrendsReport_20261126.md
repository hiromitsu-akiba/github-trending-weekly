---
layout: default
title: "GitHubトレンドリポジトリ レビュー(週間: 2026年11月26日時点)"
---

# GitHubトレンド週間レビュー（2026年11月26日時点）

## 全体トレンドの概観

AIエージェントに仕事を任せた後、計画や成果物を確認するための道具が目立つ。Plannotatorは計画と変更内容のレビュー、Open Code Reviewはソースコードの点検、Chrome DevTools MCPは実際のブラウザーの調査を担当する。Stitch Skills、Modern Web Guidance、Astryxでは、画面を作るエージェントに設計情報や実装規約を渡す使い方が共通している。

調査・日常作業・動画編集にも用途が広がっている。last30days-skillは複数の情報源を横断する調査、Nodは個人アカウントにつないだ継続作業、ffmpeg-skillは動画の編集と出力検査を扱う。AG-UIやUniverのように、自社アプリへエージェントの操作画面や編集機能を組み込む基盤も含まれる。

導入時には、自動化できる範囲と、利用者が確認すべき範囲を分けたい。ブラウザーや接続先アプリへの権限、調査結果の出典、金融データの取り込み精度、動画の最終的な見え方は、それぞれ別の確認が必要になる。スター数は注目の目安であり、品質や業務での適合性を保証するものではない。

## リポジトリ別サマリー

### 1. backnotprop/plannotator

- **リンク**：[https://github.com/backnotprop/plannotator](https://github.com/backnotprop/plannotator)
- **概要・目的**：AIエージェントが作った計画、仕様、コード変更などをブラウザーで確認し、コメントをエージェントへ返すレビュー用ツール。
- **主な特徴**：Markdown、HTML、ローカルアプリの画面、コード差分を扱う。Inboxで複数エージェントとの連絡や成果物の確認をまとめ、プラグインやMCPでも接続できる。Apache-2.0またはMITを選べるデュアルライセンス。[README](https://github.com/backnotprop/plannotator#readme)
- **想定用途・対象者**：実装前に計画を承認したい開発者、AIの変更内容をレビューする担当者、並行する作業の質問や成果物を確認する人。
- **その他特筆事項**：ローカルでレビューできることと、接続するAIや外部サービスへの通信がないことは別。連携先と共有対象の確認が必要。総スター15,083（今週+1,764）。
- **トレンド入りの理由**：公式リリースでは、コードレビュー画面の再設計、移動・名前変更を扱う意味的な差分、レビューコメントからエージェントへの相談などが案内されている。計画確認から実装後の確認まで同じ道具で扱える点は注目背景として考えられる。これらの更新と掲載の直接的な因果は未確認。[公式リリース](https://github.com/backnotprop/plannotator/releases)

### 2. google-labs-code/stitch-skills

- **リンク**：[https://github.com/google-labs-code/stitch-skills](https://github.com/google-labs-code/stitch-skills)
- **概要・目的**：Google Stitchをコーディングエージェントから利用し、画面設計と実装を進めるためのスキル・プラグイン集。
- **主な特徴**：設計、実装、補助機能に分かれ、画像や既存コードからのデザイン作成、DESIGN.mdによる設計情報の抽出、ReactやReact Nativeへの展開などを扱う。Apache-2.0。[README](https://github.com/google-labs-code/stitch-skills#readme)・[ライセンス](https://github.com/google-labs-code/stitch-skills/blob/HEAD/LICENSE)
- **想定用途・対象者**：画面の試作から実装への受け渡しを短くしたい開発者、既存サイトの見た目を整理したい担当者、複数画面のデザインをそろえたいチーム。
- **その他特筆事項**：StitchのMCP接続設定や、スキル同士の依存関係を確認する必要がある。Googleが公式サポートする製品ではない旨が明記されている。総スター12,971（今週+2,616）。
- **トレンド入りの理由**：READMEでは、設計だけで終わらせず、生成した画面を実装へ渡す一連の手順と複数エージェントへの導入方法を提供している。デザインとコードの往復を減らせる点が関心を集める背景と考えられる。今回の増加を説明する個別の公式発表は確認できていない。[公式READMEのスキル一覧](https://github.com/google-labs-code/stitch-skills#readme)

### 3. GoogleChrome/modern-web-guidance-src

- **リンク**：[https://github.com/GoogleChrome/modern-web-guidance-src](https://github.com/GoogleChrome/modern-web-guidance-src)
- **概要・目的**：コーディングエージェントへ、現在のWeb標準やブラウザー互換性を踏まえた実装指針を渡すModern Web Guidanceの原稿・評価用リポジトリ。
- **主な特徴**：HTML、CSS、ブラウザーAPI、アクセシビリティ、性能改善のガイドを備える。既存コードを調べる近代化ワークフローや評価資料も含む。コードはApache-2.0、ガイドはCC BY 4.0。通常利用向けの配布先と、この原稿リポジトリは分かれている。[README](https://github.com/GoogleChrome/modern-web-guidance-src#readme)
- **想定用途・対象者**：AIが生成したフロントエンド実装の古い書き方を見直したい開発者、互換性やアクセシビリティを確認するレビュー担当者。
- **その他特筆事項**：導入には対応するNode.js環境などが必要。匿名の利用情報送信は無効化できる。ガイドを利用しても、対象ブラウザーでの動作確認は必要になる。総スター11,029（今週+2,309）。
- **トレンド入りの理由**：11月10日の公式1.0発表では、既存コードの近代化、専門家によるレビュー、全ガイドの評価、Firefox・Edgeとの協力を案内した。単に新しい構文へ置き換えるだけでなく、複数ブラウザーで安全に改善するための材料が整った点が継続的な関心の背景と考えられる。今週の掲載の直接要因は未確認。[Chrome開発者ブログ](https://developer.chrome.com/blog/modern-web-guidance-v1)

### 4. n8n-io/nod

- **リンク**：[https://github.com/n8n-io/nod](https://github.com/n8n-io/nod)
- **概要・目的**：個人のアプリやWebサイトにつなぎ、依頼した作業を実行するn8n LabsのパーソナルAIエージェント。n8n本体とは別のアプリ。
- **主な特徴**：ローカルの作業環境とブラウザー、外部アプリ接続、継続タスクのスケジュール実行を備える。利用するAI提供元を選べ、実行側のポリシーや承認処理も設けている。Apache-2.0。[README](https://github.com/n8n-io/nod#readme)
- **想定用途・対象者**：請求書の収集、会議前の情報整理、個人用の定期確認などを、複数のアプリをまたいで自動化したい利用者。
- **その他特筆事項**：研究プレビューで、Windows・Linux版はプレビュー扱い。n8nアカウントは不要だが、AI提供元やアプリ接続サービスへの通信は発生する。利用情報送信は既定で有効。定期作業には実行環境の稼働が必要。総スター3,568（今週+1,008）。
- **トレンド入りの理由**：11月10日の公開記事で、チーム共通の業務フローを扱うn8nとは用途を分け、一人の継続的な仕事を引き受ける製品として発表した。チャットで相談する段階から、接続先で実際に仕事を終える段階への関心が注目背景と考えられる。発表日と今週の掲載は同一ではなく、掲載の直接要因は未確認。[n8n公式発表](https://blog.n8n.io/meet-nod/)

### 5. alibaba/open-code-review

- **リンク**：[https://github.com/alibaba/open-code-review](https://github.com/alibaba/open-code-review)
- **概要・目的**：コード変更やファイル群を調べ、不具合候補とその根拠を提示するAIコードレビューツール。
- **主な特徴**：差分の整理、対象ファイルの網羅状況、ルール適用、指摘箇所の位置合わせをプログラムで処理し、AIが周辺コードの検索や推論を担当する。独自モデル接続と、ホスト側エージェントへの委譲に対応。Apache-2.0。[README](https://github.com/alibaba/open-code-review#readme)
- **想定用途・対象者**：変更範囲の見落としを減らしたいレビュー担当者、既存のAI開発環境へコード点検を組み込みたいチーム。
- **その他特筆事項**：作者の評価結果を、そのまま自社コードでの精度保証とは扱えない。指摘の妥当性と、検査されなかった範囲の両方を確認したい。総スター56,355（今週+2,259）。
- **トレンド入りの理由**：公式更新では、ネイティブ実行と委譲実行のレビューに振る舞い・影響の説明を含める変更や、無効な検索正規表現をモデルへエラーとして返す修正がある。指摘生成だけでなく、レビューの根拠と失敗の扱いを整える方向は実務上の関心につながると考えられる。個々の修正がスター増加を生んだかは未確認。[公式リリース](https://github.com/alibaba/open-code-review/releases)

### 6. mvanhorn/last30days-skill

- **リンク**：[https://github.com/mvanhorn/last30days-skill](https://github.com/mvanhorn/last30days-skill)
- **概要・目的**：テーマに関連する最近の投稿、議論、公開情報を複数の情報源から調べ、出典付きの調査結果をまとめるスキル。
- **主な特徴**：Reddit、Hacker News、GitHubなどの情報源に加え、設定に応じてSNSや動画も扱う。検索計画、重複整理、コメントの収集、ローカルへの調査保存を備える。MIT。[README](https://github.com/mvanhorn/last30days-skill#readme)
- **想定用途・対象者**：技術選定の下調べ、利用者の不満の把握、勉強会や提案資料の話題探しを行う開発者・調査担当者。
- **その他特筆事項**：情報源によってAPIキー、認証、取得制限が異なる。話題性の評価と事実の正しさは別で、重要な主張は一次資料へ戻る必要がある。総スター75,093（今週+5,302）。
- **トレンド入りの理由**：11月22日のv4.6.0では、TikTokのコメント取得、TikTok・Instagramのキー不要の代替取得経路、完成した調査結果の保存機能などを更新した。投稿本文だけでなく反応や動画を含めて調査できる範囲の拡張が、関心の背景として考えられる。ただし、今回のスター増加との直接的な因果は未確認。[v4.6.0リリース](https://github.com/mvanhorn/last30days-skill/releases/tag/v4.6.0)

### 7. ChromeDevTools/chrome-devtools-mcp

- **リンク**：[https://github.com/ChromeDevTools/chrome-devtools-mcp](https://github.com/ChromeDevTools/chrome-devtools-mcp)
- **概要・目的**：AIエージェントがChromeを操作し、画面、通信、コンソール、性能情報を調べるためのMCPサーバーとCLI。
- **主な特徴**：Puppeteerによる操作、性能トレース、ネットワーク調査、CSSの確認などを提供する。画面上の問題とブラウザー内部の情報を組み合わせて調べられる。Apache-2.0。[README](https://github.com/ChromeDevTools/chrome-devtools-mcp#readme)・[ライセンス](https://github.com/ChromeDevTools/chrome-devtools-mcp/blob/HEAD/LICENSE)
- **想定用途・対象者**：Web画面の不具合調査、通信失敗時のテスト、描画や速度の問題を再現したい開発者・テスト担当者。
- **その他特筆事項**：操作対象のブラウザーには機密情報を持ち込まない運用が望ましい。利用統計と、性能調査時のCrUXへのURL照会は別の設定で無効化する。総スター59,352（今週+1,203）。
- **トレンド入りの理由**：11月24日のv1.14.0で、通信の中断・許可ヘッダーを扱うモック、Service Workerの通信・コンソール情報、計算済みCSS、新規タブを背面で開く機能などを追加した。通信異常の再現と見た目の原因調査をエージェントへ任せやすくする変更が注目背景と考えられる。掲載との直接的な因果は未確認。[v1.14.0リリース](https://github.com/ChromeDevTools/chrome-devtools-mcp/releases/tag/chrome-devtools-mcp-v1.14.0)

### 8. tradermonty/claude-trading-skills

- **リンク**：[https://github.com/tradermonty/claude-trading-skills](https://github.com/tradermonty/claude-trading-skills)
- **概要・目的**：市場の確認、銘柄調査、リスクの点検、取引記録の振り返りを支援するClaude向けスキル集。
- **主な特徴**：毎日の市場確認、週次の保有状況レビュー、取引前の確認、記録からの改善をワークフローとして整理する。API不要で始める経路と、データ提供サービスへ接続する経路を分けている。MIT。[README](https://github.com/tradermonty/claude-trading-skills#readme)
- **想定用途・対象者**：金融情報の調査を定型化したい人、判断材料と記録をそろえたい利用者。開発面では、複数スキルを順番に実行する構成の参考になる。
- **その他特筆事項**：必要な市場データやAPI契約は機能ごとに異なる。分析の出力は利益の保証や、そのまま実行する取引指示として扱えない。総スター8,451（今週+1,422）。
- **トレンド入りの理由**：公式READMEは、個別の分析スキルを列挙するだけでなく、開始手順、実行する順序、継続的な記録と振り返りまで示す。専門分野の作業を再利用可能な手順へまとめる構成が注目背景と考えられる。今回の掲載を説明する特定の公式発表は確認できていない。[公式の開始手順・ワークフロー](https://github.com/tradermonty/claude-trading-skills#readme)

### 9. ag-ui-protocol/ag-ui

- **リンク**：[https://github.com/ag-ui-protocol/ag-ui](https://github.com/ag-ui-protocol/ag-ui)
- **概要・目的**：エージェントのバックエンドと、利用者が操作する画面をつなぐためのイベント通信プロトコル。
- **主な特徴**：応答の逐次表示、ツールの実行状況、画面とエージェントの状態共有、中断・再開、子エージェントの実行元の識別を扱う。JSON Schemaと複数言語のSDKを提供する。MIT。[README](https://github.com/ag-ui-protocol/ag-ui#readme)
- **想定用途・対象者**：AIの途中経過を表示する業務アプリ、利用者の確認を挟む処理、複数エージェントの作業状況を示す画面を開発する人。
- **その他特筆事項**：通信形式をそろえても、認証、権限、切断後の再接続、イベントの重複処理などはアプリ側で設計する必要がある。総スター21,717（今週+1,421）。
- **トレンド入りの理由**：1.0仕様では、実行が成功・中断・キャンセルのどれで終わったか、子エージェントの処理をどの実行へ帰属させるかなどを明文化した。利用者が途中で介入する業務画面を作る際の共通基盤として関心を集める背景と考えられる。1.0の内容が今週の掲載を直接生んだかは未確認。[公式1.0仕様の変更点](https://docs.ag-ui.com/spec/1.0/changelog)

### 10. meta/astryx

- **リンク**：[https://github.com/meta/astryx](https://github.com/meta/astryx)
- **概要・目的**：Metaが公開する、Reactアプリ向けのUIコンポーネントと開発用ツール群。
- **主な特徴**：React 19とStyleXを基盤に、多数のUI部品、テーマ、CLIを提供する。利用側からのスタイル調整に加え、エージェントが実装規約を参照するためのガイドも用意する。MIT。[README](https://github.com/meta/astryx#readme)
- **想定用途・対象者**：業務画面の部品を統一したいReact開発チーム、人とAIで同じ部品・規約を使って画面を実装したい担当者。
- **その他特筆事項**：ベータ版。ReactやStyleX、CLIの動作条件を既存環境と照合したい。導入支援が生成するエージェント用ガイドも、既存のプロジェクト規約と合わせて確認する。総スター33,117（今週+2,635）。
- **トレンド入りの理由**：公式READMEでは、コンポーネントだけでなく、CLIやエージェント向けの参照情報を合わせて提供している。AIに自由に部品を作らせる際のばらつきを、共通のAPIと実装規約で抑えたい需要が注目背景と考えられる。今回の増加に対応する個別の公式発表は未確認。[公式README](https://github.com/meta/astryx#readme)

### 11. pookjw/HermesEnabler

- **リンク**：[https://github.com/pookjw/HermesEnabler](https://github.com/pookjw/HermesEnabler)
- **概要・目的**：Apple WatchでHermèsの文字盤を有効化するための個人向けカスタマイズツール。
- **主な特徴**：対応するwatchOS環境の機器情報を変更し、文字盤の利用条件へ働きかける。通常の文字盤アプリとは異なり、機器側の設定変更と復元手順を伴う。MIT。[README](https://github.com/pookjw/HermesEnabler#readme)・[ライセンス](https://github.com/pookjw/HermesEnabler/blob/HEAD/LICENSE)
- **想定用途・対象者**：対応OSや署名・導入方法を理解したうえで、個人所有のApple Watchの表示を調べたい技術利用者。
- **その他特筆事項**：READMEのv2はwatchOS 27.0から27.3 beta 1を対象とし、watchOS 26は非対応。アプリ削除前にMobileGestaltのバックアップを復元する注意がある。すべての機種・OSでの動作を保証するものではない。総スター2,515（今週+318）。
- **トレンド入りの理由**：現行watchOSへの対応範囲や導入・復元の説明があり、限定された文字盤を使いたい利用者の関心が背景として考えられる。ただし、今週の注目を引き起こした公式告知や出来事は確認できていない。業務向けのAI開発ツールとは用途が異なる。[作者の対応条件・注意事項](https://github.com/pookjw/HermesEnabler#readme)

### 12. we-promise/sure

- **リンク**：[https://github.com/we-promise/sure](https://github.com/we-promise/sure)
- **概要・目的**：収支、口座、資産、予算などをまとめて管理する、自己ホスト可能な個人向け財務管理アプリ。
- **主な特徴**：金融データの取り込み、分類、支出や資産の表示、外部クライアント向けAPIなどを提供する。開発が終了したMaybeをコミュニティが継承している。AGPL-3.0。[README](https://github.com/we-promise/sure#readme)
- **想定用途・対象者**：個人の財務データを自分の環境で管理したい人、金融データ連携や家計管理アプリの構成を調べる開発者。
- **その他特筆事項**：金融機関や地域によって利用できる連携が異なる。通貨・取引日の解釈、重複取り込み、バックアップと復元を確認してから利用範囲を広げたい。総スター17,927（今週+1,509）。
- **トレンド入りの理由**：11月23日のアルファ版では、支出の過去月比較に加え、取引所の時刻に基づく日付処理、取引の重複や訂正データの扱いなどを更新した。日常利用で問題になりやすいデータの整合性を改善し続ける点が関心の背景と考えられる。アルファ版の更新と掲載の直接的な因果は未確認。[公式リリース](https://github.com/we-promise/sure/releases)

### 13. dream-num/univer

- **リンク**：[https://github.com/dream-num/univer](https://github.com/dream-num/univer)
- **概要・目的**：表計算や文書の編集機能をWebアプリへ組み込むためのOffice SDK。完成したOfficeアプリを導入するだけでなく、自社の画面へ編集体験を埋め込む用途を持つ。
- **主な特徴**：データモデル、数式、描画、編集、プラグイン、コマンドと取り消し処理を備える。画面を表示せず処理する使い方にも対応する。公開コアはApache-2.0で、商用拡張とは提供範囲が分かれる。[README](https://github.com/dream-num/univer#readme)
- **想定用途・対象者**：業務データを表や文書で編集するアプリ、AIの変更案を利用者が確認・修正する画面を開発するチーム。
- **その他特筆事項**：公式の1.0製品紹介には複数種類のエディターが含まれるが、すべてがこのリポジトリだけで利用できるわけではない。必要機能のライセンス、Office形式の互換性、関連パッケージのバージョンを確認したい。総スター31,855（今週+2,319）。
- **トレンド入りの理由**：公式1.0紹介では、表計算・文書などの編集機能でプラグインとコマンドの仕組みを共有し、自社の利用者管理や業務データと組み合わせる構成を説明している。AIが作った結果を実際に編集できる業務アプリへの需要が、注目の背景として考えられる。今週の増加を直接説明する出来事は未確認。[Univer 1.0公式紹介](https://docs.univer.ai/blog/univer-1-0)

### 14. kajisho5/ffmpeg-skill

- **リンク**：[https://github.com/kajisho5/ffmpeg-skill](https://github.com/kajisho5/ffmpeg-skill)
- **概要・目的**：AIエージェントからFFmpegを使い、動画・音声の編集と、編集結果の検査を進めるためのスキル・ツール群。
- **主な特徴**：ローカルのPythonツールを備え、切り出し、結合、字幕、縦横比調整、音量調整などを扱う。入力の調査、編集、検査、出力ファイルの再確認を手順化し、HTMLのレビュー画面も生成できる。スキルはMIT、FFmpeg本体などは別のライセンス条件に従う。[README](https://github.com/kajisho5/ffmpeg-skill#readme)
- **想定用途・対象者**：研修や操作デモの録画を整える担当者、同じ編集を繰り返す人、編集条件と出力検査を記録したい開発者。
- **その他特筆事項**：FFmpeg・ffprobeなどは別途必要。長さや音声トラックを検査できても、字幕の意味、切る位置、最終的な見え方は人の確認が必要になる。総スター11,099（今週+3,048）。
- **トレンド入りの理由**：公式v4.7.0では、名前と言語を付けた複数音声トラックを出力し、実際のファイルから読み戻して確認する機能を追加した。単に編集コマンドを生成する段階から、用途に合った出力を検査する段階まで扱う点が注目背景と考えられる。掲載との直接的な因果は未確認。[公式リリース](https://github.com/kajisho5/ffmpeg-skill/releases)

レビュー対象14件／サマリー完成14件。
