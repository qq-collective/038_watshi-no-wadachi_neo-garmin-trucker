# 私の轍 — Watashi no Wadachi

> Garmin Dataをプルで集め、自分像を浮かび上がらせる。

**QQ Series** by [qq-collective](https://github.com/qq-collective)

---

## 概要

RUNNETのレース戦歴・GarminのトレーニングCSV・睡眠データを統合し、  
ランナーとしての自分を可視化するシングルHTMLアプリ。

去年のセナリ学院糸島合宿で構築した「バッチファイルに入力して管理する」プッシュ型とは違う。  
**すでにある記録を集めて見せる、プル型の自己記録ツール**

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
3. データ更新は「データ更新」タブからCSVをドロップ → グラフ即時反映
4. RUNNETにないレースは手動追加フォームから登録

### データ更新ルーティン（月1回）
```
Garmin Connect → CSVエクスポート
  → パワークエリで整形（トレッドミル除外・日付YYYY-MM-DD統一）
  → wadachi_garmin.csv として保存 → アプリにドロップ

Garmin Connect 睡眠ページ → CSVエクスポート（1年タブ）
  → wadachi_sleep.csv として保存 → アプリにドロップ
```

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
- [x] v0.2.0 — CSVドロップでグラフ即更新・手動レース追加・トレッドミル自動除外
- [ ] v0.3.0 — 主観タグ・トレラン分類・メモ機能
- [ ] v0.4.0 — 2016年〜全期間Garminデータ統合
- [ ] v1.0.0 — Webデータ検索連携チャット

---

## 哲学

> 「入力する」のではなく「整理する」。  
> データは自然に積まれている。  
> アプリが行うのはユーザーにimpresshionを与える姿に編集すること。

---

## QQ Seriesについて

日常の「もやもや」をAIとの対話でアプリに結晶化するプロジェクト。  
すべて単一HTMLファイル、Vanilla JS、GitHub Pagesで動く。

→ [qq-collective](https://github.com/qq-collective)
