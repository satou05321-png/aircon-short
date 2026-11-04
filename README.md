# aircon-short

壁掛けエアコンの分解洗浄を見せる、28秒・縦長（9:16）のショート動画の試作。
machine-skill（MIT ライセンスの無料ツール、https://github.com/AirsupHQ/machine-skill）で作成。

## ファイル

- `aircon.html` … 編集用の元ファイル（machine-skill の部品を読み込む前の状態）
- `dist/aircon.html` … そのままブラウザで開ける完成版（部品を中に埋め込み済み）

## 絵コンテ（字幕は指定どおり）

| 秒 | 映像 | 字幕 |
|---|---|---|
| 0–3 | 壁のエアコン完成形 | これが、エアコンです。 |
| 3–7 | 前面パネル・フィルター・吹出口・ルーバーが浮いて分解 | 中身を、ばらして見てみましょう。 |
| 7–10 | 断面。熱交換器（フィン）・送風ファン・ドレンパン・基盤にラベル | 汚れがたまるのは、この奥です。 |
| 10–14 | 洗浄ノズルでフィンに泡、汚れが落ちる | 工程 1/3 洗う — 奥のフィンに、汚れがびっしり。 |
| 14–18 | 汚れ水がドレンパンへ、ホースから茶色い水 | 工程 2/3 流す — 汚れた水は、外へ流します。 |
| 18–26 | 部品が戻り、きれいな風の矢印 | 工程 3/3 仕上げ — 組み戻せば、きれいな風。 |
| 26–28 | 完成形＋小さく「分解洗浄、承ります」 | エアコンは、年に1回の分解洗浄を。 |

## Windows で高画質（1080×1920）の MP4 を書き出す

前提：Node.js（LTS）と ffmpeg が入っていること。

1. machine-skill を入れる：`npx skills add AirsupHQ/machine-skill -g -a claude-code`
2. 作業フォルダを作り、その中に `dist\aircon.html` を置く
3. そのフォルダで `npm i -D playwright` → `npx playwright install chromium`
4. 書き出し：
   `node %USERPROFILE%\.claude\skills\machine\scripts\record.mjs aircon.html out\aircon.mp4 --w 1080 --h 1920`

GPU のない環境では非常に遅いので、`--q lite=1`（陰影処理を省く）を付けると速くなる
（`--q` はこの試作で追加したオプション。公式版の record.mjs には無い場合がある）。
