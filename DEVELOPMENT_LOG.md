# Development Log: Knitting Remapper

## 1. プロジェクトの核心 (Core Philosophy)
* **Systematic Integrity (論理的誠実さ):** 表面的な美しさやAd-hocな修正を排し、正しい計算プロセスから導かれる結果を絶対とする。
* **Flux Engine (誤差拡散):** 計算途中での「早期の丸め（Premature Rounding）」を禁止。最終出力の直前まで物理制約（整数）を適用せず、連続値（Float/幾何学的正解）を保持する。
* **Cognitive Chunking (認知的チャンク化):** 出力結果は、人間の認知的負荷を下げるため、規則性に基づいてグループ化し、直感的に理解できる形式で提示する。
* **Universal Tool (普遍性):** 特定パターン（例: Sumac）専用機にしない。パターン名はあくまで「検証用コンテキスト」として分離し、計算ロジック自体は汎用的なスキーマを持つ。

## 2. バージョン定義: v23.2 (Re-Initialization)
* **ステータス:** 環境初期化完了 / 仕様再定義
* **UI仕様 (Source Matrix):**
  * 起動時に詳細な入力マトリクスを表示。
  * 「検証用プリセット（Sumac）」が自動ロードされ、即時検証可能な状態で立ち上がる。
* **構造仕様 (Construction Schema):**
  * **Phase A:** Flat Start (往復編みでの背面・袖の増し目)
  * **Phase B:** Neck Bridge Join (前衿ぐりの結合ロジック)
  * **Phase C:** Round Transition (輪編みへの移行)

## 3. ロジック・アーキテクチャ (Logic)
* **Flux Distribution:**
  増し目を整数の段数に割り振る際、剰余（余り）を切り捨てず、次の区間へ「誤差」として拡散させるアルゴリズム。
* **Interpolation:**
  サイズ間の数値を線形補間し、ターゲット寸法を幾何学的に算出する。

## 4. ロードマップ (Roadmap)

### Phase 0: Genesis (完了)
- [x] 環境の完全初期化 (Mac, Mobile, GitHub)
- [x] リポジトリの作成と航海日誌の策定

### Phase 1: Foundation (基盤構築)
- [ ] **Server Setup:** Node.js + Express の最小構成を作成。
- [ ] **Core Logic:** `FluxEngine` クラスの実装（丸め処理の排除）。
- [ ] **Test Route:** コンソール上で計算結果が正しいか確認するルートを作成。

### Phase 2: User Interface (UI復元)
- [ ] **Source Matrix:** HTMLフォームの作成とSumacプリセット値の埋め込み。
- [ ] **Response View:** 計算結果を「認知的チャンク」に基づいて表示するビューの実装。

### Phase 3: Verification (検証)
- [ ] **Browser Test:** ブラウザでSumacの設計数値を入力し、出力が設計書と一致するか検証。
- [ ] **Printing:** 印刷プレビューのスタイル調整。

## 5. ログ (Change Log)
* **2026-02-03 (v23.2 Genesis):** * プロジェクト環境を全消去し、Tabula Rasa（白紙）から再始動。
  * 航海日誌を再定義。開発の優先順位を「論理的整合性」に固定。