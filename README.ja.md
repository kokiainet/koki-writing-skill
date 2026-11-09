# Koki Writing Skill

[![English](https://img.shields.io/badge/English-2563EB?style=for-the-badge)](README.md) [![简体中文](https://img.shields.io/badge/简体中文-DC2626?style=for-the-badge)](README.zh-CN.md) [![日本語](https://img.shields.io/badge/日本語-7C3AED?style=for-the-badge)](README.ja.md)

話したアイデアを、自分の声のままの記事に変えるためのスキルです。根拠、実際の画像、WeChatに貼れるRaphaelレイアウト付きで仕上げます。

私自身のクリエイター向けワークフローを切り出し、カスタマイズ可能な公開版としてまとめた単独のスキルです。本READMEは日本語で読めます。スキル本体の手順とワークフロー資料は英語と簡体字中国語で提供しています。

## 完成イメージ

**英語の台本が、読みやすい英語の記事になります。** 下は私の英語記事「What the Midterms Mean for America’s AI Race」の抜粋を実際にスマホで表示したもので、出典メモと英語のコピーボタンが付いています。

<p align="center">
  <img src="docs/media/article-opening-en.jpg" width="375" alt="実際の英語記事：英語の見出し、本文、出典メモ、記事コピーボタン">
</p>

| 用意するもの | 得られるもの |
| --- | --- |
| 話した内容の転写、アイデア、下書き | 言い回しと立場を保った、編集可能な記事 |
| 裏付けが必要な主張やトピック | 出典、関連する実際の画像、キャプション |
| レイアウトの好み | コピーしてWeChatに貼れるボタン付きのRaphaelレイアウト |

英語の例をそのまま試せます：[元の台本の抜粋](examples/source-script-en.txt) → [記事のMarkdown](examples/article-en.md) → [Raphael HTML](examples/article-preview-en.html)。HTMLをダウンロードしてブラウザで開くと、**記事をコピー**を試せます。スクリーンショットとダウンロードできるファイルは、同じ英語の抜粋を表示しています。

## クイックスタート

### 1. ツールを準備する

Codex、またはテキスト／ファイルにアクセスできるAgent Skills互換エージェントを使います。調査と実際のWeb画像にはブラウジングが必要です。レイアウトには [Raphael Publish](https://publish.raphael.app/) を使い、同梱の任意のローカルアダプタにはNode.js 20+と `jsdom` 26.1.0が必要です。執筆だけなら動画エディタは不要です。

### 2. このスキルをインストールする

Codexに次を貼り付けます。

```text
$skill-installer 次の場所からスキルをインストールしてください：
https://github.com/kokiainet/koki-writing-skill/tree/main/skills/koki-wechat-article
同名のスキルが既にある場合は保持し、上書きする前に競合を報告してください。
```

インストール後に新しいチャットを開始し、`$koki-wechat-article` で呼び出します。他のAgent Skills互換ツールでも、完全な `skills/koki-wechat-article` フォルダを各自の方法でインストールできます。[Codexのスキルドキュメント](https://learn.chatgpt.com/docs/build-skills)も参照してください。

### 3. 素材を渡す

転写／下書きを貼り付けるか、テキストファイルを添付します。必ず残したい言い回し、確認済みの出典リンク、希望するタイトル、画像フォルダも一緒に渡してください。音声入力の粗い転写から始められます。完成済みの下書きをレイアウトだけに使うこともできます。

### 4. 最初の記事を作る

```text
$koki-wechat-article を使ってください。
入力：私が添付した転写。
言語：英語。私の声、意見、意味のある繰り返しを残してください。
名前と事実主張を確認し、出典付きで関連する実際の画像を追加してください。
Raphaelのsspaiテーマを使い、スマホでの読みやすさを確認してください。
編集可能なMarkdown、ローカルのレイアウトHTML、WeChat用リッチテキスト、画像、出典メモを納品してください。
下書きは ./outputs/my-article/ に保存してください。
```

自分の素材を用意する前に試したい場合は、エージェントに `examples/source-script-en.txt` を指定し、その抜粋から英語のレイアウトを作るよう依頼してください。

### 5. 修正して使う

```text
本文と承認済みの画像は変えないでください。
スマホで読みやすくするために、段落、見出しの階層、強調、画像の配置だけを調整してください。
```

納品されたレイアウトHTMLをブラウザで開く → **記事をコピー**をクリック → WeChatのエディタに貼り付け → 画像と最終的な見え方を確認 → 準備ができたら公開、という流れです。Markdownはその後の修正用に編集可能なまま残ります。

| 納品物 | 用途 |
| --- | --- |
| Markdown | テキストの編集を続ける |
| レイアウトHTML＋WeChat用リッチテキスト | 整形済み記事のプレビューとコピー |
| 画像と出典の記録 | 根拠の追跡と、関連素材の再利用 |

任意のローカルアダプタを使う場合は、リポジトリのルートで `npm install --ignore-scripts` を実行し、[完全なレンダリングコマンド](skills/koki-wechat-article/references/raphael.md)に従ってください。対応する公式エンジンは別途ダウンロードします。

## 自分仕様にする

[creator.example.yaml](creator.example.yaml) を作業プロジェクト内に `creator.local.yaml` としてコピーし、名前、メディアのフォルダ、好みを記入します。エージェントはこのファイルを読みますが、アカウントに接続したり自動で実行したりはしません。私物のメディアや締めの文言が不足している場合は、元の作者のものを借用せず、スキップするか報告します。[PRIVACY.md](PRIVACY.md)も参照してください。

## ツール

[Raphael Publish](https://publish.raphael.app/)、または同梱の[ローカルアダプタ](skills/koki-wechat-article/references/raphael.md)を使います。任意のアダプタにはNode.js 20+と `jsdom` 26.1.0が必要で、リポジトリのルートで `npm install --ignore-scripts` を実行します。対応するRaphaelバンドルは公式の配布元から別途ダウンロードしてください。このリポジトリでは再配布していません。

## Kokiについて・連絡先

作成：**Koki**（Anti-Distill Skillの作者、Social Codingの提唱者）。

[Website](https://kokiai.net/) · [X / Twitter](https://x.com/kokiainet) · [Instagram](https://www.instagram.com/kokiainet/) · [YouTube](https://www.youtube.com/@kokiainet) · [LinkedIn](https://www.linkedin.com/in/koki-x-309815217/) · [Substack](https://kokimemo.substack.com/)

コラボレーションや質問は [X](https://x.com/kokiainet) か [LinkedIn](https://www.linkedin.com/in/koki-x-309815217/) でメッセージをください。スキルの不具合や提案は、このリポジトリのIssueでお願いします。私物のメディアやアカウント情報は公開Issueに書かないでください。

## 他のクリエイター向けスキル

- [Koki Short Video Skill](https://github.com/kokiainet/koki-short-video-skill)
- [Koki Long Video Skill](https://github.com/kokiainet/koki-long-video-skill)

## ライセンス

オリジナルのスキル手順とアダプタコードは [MIT](LICENSE) ライセンスです。サードパーティの製品、フォント、メディア、サービスには、それぞれのライセンスと規約が適用されます。

デモメディアはワークフローの紹介用に含まれています。映像素材、肖像、サードパーティ抜粋の権利は各権利者に帰属し、MITのコードライセンスでは許諾されません。[素材の詳細](docs/media/README.md)を参照してください。
