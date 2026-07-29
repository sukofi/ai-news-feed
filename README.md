# ai-news-feed

`ai-news` アプリ（大人向けAIニュース5本）の**配信先**。

このリポジトリは記事データを置くだけの静的な入れもの。
アプリはここの `articles.json` を GitHub Pages 経由で取りにくる。

```
https://sukofi.github.io/ai-news-feed/articles.json
```

## 直接編集しない

`articles.json` の生成元は `ai-news` リポジトリの `assets/data/articles.json`。
更新は必ず `ai-news` 側から流す。

```bash
./tools/publish_feed.sh    # 検査 → テスト → コピー → push → 配信ずみを記録
```

ここを手で書きかえると、次の配信で上書きされて消える。

## 中身

| ファイル | 何か |
| --- | --- |
| `articles.json` | その日の記事5本（`generatedAt` と `articles`） |
| `.nojekyll` | GitHub Pages の Jekyll 処理を切る |
| `index.html` | 配信が生きているか目で確かめるためだけのページ |

## 決めごと

- 画像は持たない。文字だけ。
- 記事には必ず出典（`source`）がつく。本文の転載はしない。
- 個人情報も端末IDも受けとらない。アプリが送るのは ETag だけ。
