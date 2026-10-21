# keirin-platform

競輪のレースデータを集めて、**競走得点をより正確に読む**ための個人プロジェクトです。

**[競輪マルチビューアー](https://keirin-platform.github.io/keirin-multiviewer/)** — 各競輪場の公式 YouTube ライブを、1つの画面に最大4枠で並べて見られます。ミッドナイトなどで、いくつもの場が数分おきに発走するときに。

## 取り組んでいること
- **昇級・降級を補正した競走得点** — 競走得点は「当月＋前3ヶ月」の平均で、級班が変わっても前の級班で取った点がそのまま入ります。S級とA級で得られる点の水準が違うぶんを補正します。
- **相手の強さを考慮したレーティング** — 「誰に先着したか」から実力を推定します（Plackett–Luce モデル）。
- **競輪の通説の検証** — 地元有利、7車立てと9車立て、車番、バンクと決まり手などを、データで確かめます。
- **分析記事** — 結果は記事にまとめる予定です（準備中）。
- **競輪マルチビューアー** — 複数の場のライブ配信を、タブを切り替えずに見るためのページです。

## 仕組み
- サーバーを持たずに、GitHub Actions で毎日データを集めています。サイトへの負荷を抑えるため、リクエストは1件ずつ、間隔を空けて送ります。
- Python（uv、httpx、DuckDB、NumPy）、GitHub Actions、Streamlit
- 競輪マルチビューアーは、GitHub Pages の静的ページです。配信の一覧は、GitHub Actions が YouTube Data API で各場の公式チャンネルを調べて作ります。

## リポジトリ
| リポジトリ | 内容 |
|---|---|
| [keirin-platform](https://github.com/keirin-platform/keirin-platform) | 収集、昇降級補正、レーティング、分析のコード |
| [keirin-multiviewer](https://github.com/keirin-platform/keirin-multiviewer) | 競輪マルチビューアー（各場の公式 YouTube ライブを並べるページ） |

コードは [MIT ライセンス](https://github.com/keirin-platform/keirin-platform/blob/main/LICENSE)で公開しています。

## お断り
- 個人の非営利のプロジェクトで、JKA や競輪場など公式とは関係ありません。
- データの出典は [KEIRIN.JP](https://keirin.jp/) です。収集したデータは私的利用の範囲にとどめ、公開していません。
- 車券の購入をすすめるものではありません。
- 競輪マルチビューアーは、各場が YouTube で公開しているライブ配信を、YouTube の埋め込みプレーヤーで並べているだけです。KEIRIN.JP のデータは使っていません。
