# 米沢みさわ小学校｜とここと ウェブサイト

Claude のアーティファクト（「とここと サイト再現モック」「日帰りプランをえらぶ」）を、
GitHub Pages でそのまま公開できる静的サイトにしたものです。

| ファイル | 内容 |
| --- | --- |
| `index.html` | トップページ（とここととは／泊まる／体験する／新しい取り組み／アクセス） |
| `daytrip.html` | 日帰りプランをえらぶページ（人数・日付から合計料金を計算 → 予約ページへ） |
| `data/daytrip-plans.json` | 日帰りプランのデータ（名前・料金・空き状況・写真・当日の流れ） |
| `imgs/` | 写真を置くフォルダ |

## 公開のしかた（GitHub Pages）

1. GitHub のリポジトリ → **Settings** → **Pages**
2. **Source** を「Deploy from a branch」、ブランチを `main`（フォルダは `/ (root)`）にして **Save**
3. 数分後に `https://<ユーザー名>.github.io/tokocoto-website/` で見られます

## 写真を入れる

`imgs/` に次の名前で画像をアップロードすると、自動で差し替わります（無い間は「[写真]」の枠が出ます）。

- トップページ：`hero.webp` / `stay-whole.webp` / `stay-dorm.webp` / `stay-room.webp` /
  `exp-sukiyaki.webp` / `exp-gym.webp` / `exp-imo.webp` / `exp-gamaguchi.webp` / `oshinui.jpg`
- 日帰りプラン：`data/daytrip-plans.json` の `imgUrl` に書いたパス（例：`imgs/bbqset.webp`）

## 日帰りプランを編集する

- **いちばん簡単**：`daytrip.html?edit=1` を開く → 「編集する」で料金・空き状況などを直す →
  「JSONを書き出す」で出た `daytrip-plans.json` を GitHub の `data/` に上書きアップロード。
  （編集中の内容はその端末に下書き保存されるだけで、他の人には見えません）
- **写真**：編集中にカードをクリックして Ctrl+V で貼り付け、またはカードにドラッグ＆ドロップ／「写真を選ぶ」。
  写真は自動で縮小されて JSON に入るので、上の手順で JSON を上書きするだけで写真も公開されます。
- または GitHub 上で `data/daytrip-plans.json` を直接編集してもOKです。
  - `mode`：`per` = 1名あたり、`flat` = 1組・1枠定額
  - `price`：料金（未定なら `null`）
  - `stat`：`ok` = 空きあり、`ng` = 満室、`off` = 対象外

## 予約ボタンの行き先

`daytrip.html` の先頭付近にある `RESERVE_URL` が「予約に進む」の行き先です。
tripla の予約ページURLが決まったらここを差し替えてください。
