# CLAUDE.md

このファイルは、このリポジトリで作業する Claude Code 向けのガイドです。人向けの説明は `README.md` にある。

## プロジェクト概要

生成AIパスポート試験の学習サイト **「生成AI用語ドリル」**。運営者は Yuki-fe（個人・副業）。`cloud-drill`（クラウド用語ドリル）の build.py をもとに作った。FE用語ドリル（`claude FE対策サイト`）・ITパスポート用語ドリル（`ip-drill`）なども同じ運営者。

- **サイト**: https://genai.yogo-drill.com/ （予定。GitHub Pages。リポジトリ `yuki-fe/genai-drill` の `main` ブランチの `/docs`。公開するときは Xserverドメインの DNS に `genai` の CNAME（`yuki-fe.github.io`）を足す）
- 用語の単語帳（カード・4択・書いて答える・復習・一覧）、用語ごとの解説ページ、章別ミニテスト（`test.html`、5章から4問ずつ20問）、略語クイズと早見表（`abbr.html`）
- 用語は `data/make_terms.py` に書き、実行して `data/terms.json` を作る。出題範囲は GUGA の「生成AIパスポート試験シラバス（2027年2月試験より適用）」の5章と詳細キーワード（https://guga.or.jp/assets/syllabus.pdf 、2026年10月に確認）
- 試験はオンライン（IBT）で60分・60問、年5回（2・4・6・8・10月）。2026年10月試験までは旧シラバス
- お問い合わせは FE と同じ Google フォーム https://forms.gle/s4yB1xMbcoRqZps2A

## よく使うコマンド

```powershell
python data/make_terms.py               # 用語を直したら
python build.py                         # docs/ を作り直す
python -m http.server 8000 -d docs      # http://localhost:8000 で確認
```

## 決まりごと

- ユーザーへの回答は **日本語**。運営者は初心者寄りなので、手順は画面のボタン名まで具体的に書く
- サイト名に「生成AIパスポート」を入れない（実施団体の資格の名前）。「公式」など実施団体と関係があるように見える言葉、「必ず合格」など確かめられない言い切りは使わない。フッターの注意書きを消さない
- シラバスは毎年のように改訂される。改訂が出たら用語を見直す。商品・モデルの名前やバージョン、料金は書かない（すぐ変わる）
- 法律・ガイドライン（AI法、AI事業者ガイドライン、個人情報保護法、著作権法など）の内容を足すときは、元の文書で確かめる
- `docs/` は生成物。直接編集しない（GitHub Pages が使うので commit はする）
- 公開後は用語の id（並び順）を変えない。新しい用語は `TERMS` の最後に足す
- localStorage の名前は `genai-drill-` で始める
- 広告は「PR」の表示を消さない。トークン・個人情報はリポジトリに入れない（リポジトリは公開）
- 手順書・計画などの資料は FE 側の `notes/`（公開しない）で作る
