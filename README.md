# 🍽 Food Score

食べ物をクリックして選ぶと、選択した合計スコアをリアルタイムで表示する Web アプリ。バニラ JavaScript（ES6 クラス）と DOM 操作だけで実装しています。

## ✨ 機能

- 食べ物カード（`.food`）をクリックして選択／解除
- 選択中の食べ物のスコア（`.food__score`）を合計して表示
- クリックのたびに合計スコア（`.score__number`）を再描画
- 何度でも選び直せるトグル方式

## 🛠 技術スタック

| 項目 | 内容 |
| --- | --- |
| 言語 | JavaScript (ES6+) |
| 設計 | クラスベース / Singleton パターン |
| DOM 操作 | ブラウザ標準 API（フレームワークなし） |
| スタイリング | CSS（BEM 記法） |

## 🚀 ローカルで動かす

```bash
git clone https://github.com/your-username/food-score.git
cd food-score
```

`index.html` をブラウザで開く。

## 📁 ディレクトリ構成

```
food-score/
├── index.html      # 食べ物カード・スコア表示のマークアップ
├── style.css       # スタイル（.food / .food--active / .score__number）
└── script.js       # Score / Food / Foods クラス
```

## 💡 実装のポイント

- **Singleton パターン**で `Score`・`Foods` を `getInstance()` から単一インスタンスとして管理し、どこからでも同じ状態を参照
- **責務を分けたクラス設計**：`Food`（個々の要素）/ `Foods`（要素の集合）/ `Score`（合計の表示）
- `addEventListener` + `bind(this)` でクリックイベントを登録し、`this` を要素に束縛
- `classList.toggle("food--active")` で選択状態を切り替え
- **getter**（`get activeElements` / `get activeElementsScore` / `get totalScore`）で派生した状態を都度計算し、状態の二重管理を回避
- `reduce` で選択中スコアの合計を算出
- DOM の `textContent` を `Number()` で数値化してから集計
- クラス名は **BEM 記法**（`food__score`・`food--active`・`score__number`）で統一

## 🔧 今後の改善案

- リセットボタン（全選択の解除）
- 選択中の食べ物の件数・一覧表示
- 合計スコアの目標値・上限を設定して達成度を表示
- `localStorage` で選択状態を保存
- **TypeScript 化**で型安全に
- テスト（Jest など）の追加
