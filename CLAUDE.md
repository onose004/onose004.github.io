# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## このリポジトリ

小野瀬良佑の個人サイト（https://onose004.github.io）。`index.html` 一枚 + `images/` のみ。ビルド・CI・テストは無い。

## 運用上の注意

- **`master` への push が本番公開。** GitHub Pages が `master` を直接配信する。ステージングは無い。
- **GA タグ (`G-P7VDY7BRCE`) を消すときはフッタの開示文もセットで消す。** 逆も同様。
- **プレビューはブラウザで `index.html` を開くか `python3 -m http.server`。**

## Claude Code 設定

`.claude/settings.json` で `Bash(git commit:*)` と `Bash(git push:*)` を `ask` にしている（誤操作による本番反映を防ぐため）。自動で commit / push しないこと。
