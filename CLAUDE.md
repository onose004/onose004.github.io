# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## リポジトリの目的

小野瀬良佑の個人サイト。GitHub Pages により https://onose004.github.io で公開されている単一ページで、プロフィール・研究業績・学歴・連絡先を掲載する。

## アーキテクチャ

- **単一ファイル構成。** マークアップとコンテンツはすべてリポジトリ直下の `index.html` に収まっている。ビルドステップ、パッケージマネージャ、サーバサイドコードは存在しない。
- **スタイル。** Tailwind CSS を CDN (`cdn.tailwindcss.com`) から読み込み、インラインの `tailwind.config` で `sans` / `serif` のフォントスタックを Courier monospace に上書きしている。ベースの `font-size` は 12px。スタイル変更は原則 Tailwind のユーティリティクラスで行い、ユーティリティで表現できない場合のみ既存の `@layer base` ブロック内に生 CSS を追加する。
- **アセット。** 静的画像は `images/` に配置する（favicon `icon.png`、フッタの `smile.png`）。相対パスで参照する。
- **アナリティクス。** Google Analytics (`G-P7VDY7BRCE`) を `<head>` に設定しており、フッタに必要な開示文を置いている。タグを外すときは開示文も同時に外すこと。
- **デプロイ。** `master` ブランチが GitHub Pages により自動公開される。`master` への push ＝本番反映であり、ステージング環境も CI も存在しない。

## コンテンツの書き方

- **日英バイリンガル。** ページは日本語と英語が混在する。セクション見出しは `日本語 (English)` の形式（例: `研究業績 (Publications)`）。新しいセクションを追加する際もこのパターンを踏襲する。
- **研究業績。** `研究業績` 配下は固定の小セクション（学位論文 / 著書 / 論文 / 国際会議 / シンポジウム・ワークショップ / 支部大会 / 受賞 / 研究助成）に分かれている。業績を追加するときは該当する `<section>` 内に `<li>` を追加し、既存の書式（著者名のうち小野瀬を `<strong>` で囲む、タイトル、掲載誌・会議、外部リンクは `class="text-blue-600 hover:underline"` と `target="_blank"` 付きで `[Link]` / `[DOI]` / `[YouTube]` として記載する）に合わせる。

## ローカルプレビュー

ビルド不要。`index.html` をブラウザで直接開くか、任意の静的サーバ（例: `python3 -m http.server`）でディレクトリを配信して push 前に確認する。

## コミットの方針

`/home/onose/CLAUDE.md` に従う: Conventional Commits を優先し、メッセージは一行に収め、Claude Code の署名は含めない。

## Claude Code 設定

- `.claude/settings.json` をリポジトリに含めている。`git commit` と `git push` は `ask` に設定してあり、実行前にユーザーの承認を求める。Claude Code はこの設定を尊重し、自動で commit / push しないこと。
