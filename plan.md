# OANDA機能代替 実装計画（Draft）

## 目的

GitHub Pages 上で表示できない OANDA 埋め込みウィジェットの代替として、
同等の意思決定に必要な情報を **静的配信可能な構成** で提供する。

## 対象機能（元OANDA）

1. Order Book
2. Volatility
3. Value at Risk
4. Price Comparison
5. VaR on Chart

## 代替方針（機能マッピング）

### 1) Order Book
- 代替名: `Market Pressure`
- 算出: 期間内の日次リターンが正/負となる件数比率
- 表示: BUY/SELL バー（%）
- 備考: 実板データではなく、センチメント近似指標

### 2) Volatility
- 代替名: `Historical Volatility (20d)`
- 算出: 20営業日リターン標準偏差 × √252
- 表示: 年率%（小数点2桁）

### 3) Value at Risk
- 代替名: `Historical VaR`
- 算出: 日次リターン分布の 5% / 1% 分位点（95%/99%）
- 表示: 損失率%（絶対値）

### 4) Price Comparison
- 代替名: `Cross Rate Comparison`
- 算出: 取得レートから GBP/JPY, USD/JPY, EUR/JPY を同時表示
- 表示: テーブル形式

### 5) VaR on Chart
- 代替名: `Price + VaR Threshold`
- 算出: GBP/JPY 終値時系列 + 最新価格 × (1 - 95%VaR)
- 表示: SVGラインチャート + VaR水平ライン

## データ設計

- 一次データ: Frankfurter API (`GBP -> JPY, USD, EUR`)
- 取得期間: 直近約120日
- 最低必要データ数: 30点（不足時はエラー表示）
- 更新タイミング: ページロード時

## UI設計

- 1行目: Order Book代替 / Volatility / VaR / Price Comparison
- 2行目: VaR on Chart
- 補助: TradingView（Technical Analysis / Events）
- ステータス表示: 取得中 / 成功 / 失敗

## 例外・障害時

- API失敗: カードに「取得失敗」表示
- データ不足: `insufficient data` として扱う
- 失敗時でもページ全体は表示継続

## 今後の拡張案

- 期間切替（20/60/120日）
- 指標切替（GBP/JPY 以外）
- 疑似Order Bookの重み付け改善（直近重視）
- 計算ロジックを `script.js` 分離して保守性向上

## 受け入れ条件（Acceptance Criteria）

- [ ] GitHub Pages 上でエラーなく描画される
- [ ] 5機能の代替カードが全て表示される
- [ ] API失敗時にUIが崩れず、失敗メッセージが表示される
- [ ] README と本計画書の説明内容が一致している
