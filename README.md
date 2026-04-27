# 私の轍 — Watashi no Wadachi

> 自分の後に路はできる。走った記録をプルで集め、自分像を浮かび上がらせる。

**QQ Series** by [qq-collective](https://github.com/qq-collective)

---

## 概要

RUNNETのレース戦歴・GarminのトレーニングCSV・睡眠データを統合し、  
ランナーとしての自分を可視化するシングルHTMLアプリ。

去年の「入力して管理する」プッシュ型とは違う。  
**すでにある記録を集めて見せる、プル型の自己chronicle。**

---

## 機能

| タブ | 内容 |
|------|------|
| 概観 | プロフィール統計・フルマラソン推移・全レースタイムライン |
| 練習×睡眠 | 月間走行距離×睡眠スコア・レース前4週分析・心拍推移 |
| レース戦歴 | 全出走記録テーブル（PB自動マーク） |
| 診断 | A/B/C/D判定＋データに基づく総合所見 |
| チャット | データ参照AI（Anthropic Claude API） |
| データ管理 | GarminCSV・睡眠CSVのアップロード口 |

---

## データソース

- **レース記録** — RUNNETマイページよりコピペ
- **練習ログ** — Garmin Connect「CSVをエクスポート」
- **睡眠データ** — Garmin Connect 睡眠ページ「CSVをエクスポート」

すべて手動エクスポート。外部APIへの自動連携なし。  
**セキュリティファースト：認証情報はアプリに渡さない設計。**

---

## 使い方

1. `watashi_no_wadachi.html` をブラウザで開く
2. チャット機能を使う場合は「チャット」タブでAnthropicのAPIキーを入力
3. データを更新する場合は「データ管理」タブからCSVをアップロード

### APIキーについて
- [Anthropic Console](https://console.anthropic.com/) で取得
- `sk-ant-` から始まるキー
- localStorageに保存（外部送信なし）

---

## 技術スタック

- Vanilla JS / 単一HTMLファイル
- Chart.js 4.4.1（CDN）
- Google Fonts（Noto Serif JP / Space Mono）
- Anthropic Claude API（`claude-sonnet-4-20250514`）
- GitHub Pages対応

---

## ロードマップ

- [x] v0.1.0 — 6タブ基本動作・全データ統合・チャット
- [ ] v0.2.0 — CSVアップロードでデータ動的更新
- [ ] v0.3.0 — 主観タグ・シューズ管理・トレラン分類
- [ ] v0.4.0 — 2016年〜全期間のGarminデータ統合
- [ ] v1.0.0 — Webデータ検索連携チャット

---

## 哲学

> 「入力する」のではなく「浮かび上がらせる」。  
> データは走ることで自然に積まれている。  
> アプリはそれを見えるようにするだけでいい。

---

## QQ Seriesについて

セナリ学院発、日常の「もやもや」をAIとの対話でアプリに結晶化するプロジェクト。  
すべて単一HTMLファイル、Vanilla JS、GitHub Pagesで動く。

→ [qq-collective](https://github.com/qq-collective)
