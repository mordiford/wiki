<!-- TITLE: Madoka -->
<!-- SUBTITLE: マジメインヒロイン -->

# madoka

- 主にカスタムROMのビルド実行用スクリプトです。  
- [優秀なマネージャー](http://aokana.net/character/sub/#character5)のつもりですが、セットアップまではしてくれません。  
- [LineageOS/CM14.1 のビルド方法 - dev:mordiford](https://dev.maud.io/entry/2016/12/28/howto-build-lineageos-14/) とかを参考に実施してください。

# 機能

- 対話型ではないので一度実行すれば終了まで操作不要
- 実行時オプション： ROM(ディレクトリ)・ビルドターゲット・ツイート可否・ `repo sync` 可否・ `make clean` 可否・プライベートビルドの可否 を引数で指定
- ログの保存、ビルド成否による保存先の振り分け
    * `log/success` と `log/fail` に振り分けられます
- 複数種類のカスタムROMに対応可能
    * とりあえずLineageOS(CyanogenMod)とAndroid Ice Cold Projectのフォーマットに対応しています
    * バージョン上がってもだいたい取れるようにはしてます
- ビルド開始・終了時のSNS投稿機能(Twitter/Mastodon/Pushbullet)
- クラウドストレージへのアップロード
- 成果物の移動

# 用法

```bash
git clone https://github.com/lindwurm/madoka.git -b nextcloud
```

- ディレクトリ構造の例は以下(`/log`以下と`~/rom`は実行時に作成されます)
    * `~/build` の名前はスクリプトに関係しませんのでご自由にどうぞ
    * **要するにROMのソース置いたディレクトリと同じ階層に`madoka`を置いてください**

```
~/
|
|-- build/
|   |-- aicp/
|   |-- du/
|   |-- lineage/
|   |-- log/
|   |   |-- fail/
|   |   `-- success/
|   `-- madoka/
|       |-- build.sh
|       |-- LICENSE
|       `-- README.md
|-- oysttyer/
|   `-- oysttyer.pl
|-- rom/  
|   `-- ${device}/
`-- ./cloud-dl
```

実際の使い方は以下の通りです。

```bash
./build.sh [ROMのディレクトリ名] [ビルドターゲット] [オプション]
```

## オプション一覧

option | 詳細
---|---
`-t` | oysttyerを用いてツイートします。事前にアカウント設定をoysttyerで行ってください。
`-s` | `repo sync` を行います。デフォルトのジョブ数は8なので適宜スクリプト本体いじって加減してください。
`-c` | `make clean` をビルド前に行います。
`-x` | プライベートビルドモードを有効にします。詳しくは後述。

例えば `hammerhead` 向けのAICPをツイート有、repo sync有、make clean有でビルドする場合は

```
./build.sh aicp hammerhead -t -s -c
```

です。

## SNS連携

### Twitter (開始/終了時)

- [oysttyer](https://github.com/oysttyer/oysttyer) に丸投げしています。別途セットアップは済ませておいてください
- デフォルトのハッシュタグは `#madokaBuild` ですが、各自で使う際はハッシュタグを変えといてください
    - 冒頭の `$TWEET_TAG` の値を適当に

### プッシュ通知 (終了時)

- [Pushbullet](https://www.pushbullet.com/) APIを使用しています
    - アクセストークンの発行が必要です
    - デフォルトでは自分から自分へのメッセージ扱いになるんですが、Channel作って `channel_tag` とか使うと自分の持ってるチャンネルに投げることとかもできます(なおpublicになります)
        - 例: [@mashiro-build](https://www.pushbullet.com/channel?tag=mashiro-build)
        - 詳しくは [Pushbullet API](https://docs.pushbullet.com/#create-push) 読んでください

### Mastodon対応

- `npm install -g toot` とかで [glynnbird/toot](https://github.com/glynnbird/toot) を入れているとトゥートできます。

## クラウドストレージへのアップロード

### Nextcloud へのアップロード

- **[nextcloud](https://github.com/lindwurm/madoka/tree/nextcloud)** ブランチを使用してください
- https://github.com/cghdev/cloud-dl を使用します。セットアップが必要です
- 今のところ一番シンプルかつ問題が少ないので良いです

<details>
<summary>現在はサポートされていないバージョン（畳まれています）</summary>

### Google Drive へのアップロード（outdated）

- **[gdrive](https://github.com/lindwurm/madoka/tree/gdrive)** ブランチを使用してください
- https://github.com/prasmussen/gdrive を使用します。セットアップが必要です
- 他にもフォルダIDの取得・スクリプト内への記入が必要です（めんどい）。
    - build.sh 本体に必要な説明は書いたので読んでください。
    - 手元で対応機種増やすたびにアップロード先のフォルダID書いていくのだるくなってdrop

### [MEGA](https://mega.nz) へのアップロード（outdated）

- **[mega](https://github.com/lindwurm/madoka/tree/mega)** ブランチを使用してください
- MEGAのアカウント及び別途 [megatools](https://megatools.megous.com/) のセットアップが必要
- [共有リンクを発行したフォルダにアップロードすると他のユーザから読めない](https://github.com/megous/megatools/issues/54) 既知の問題が3年半くらい直ってないのであんまりおすすめしてない。

</details>

## ファイル移動

- ビルド完了後に別ディレクトリへROMの `.zip` を退避
    - デフォルトでは `~/rom` になっています
    - 連続で複数機種ビルドする際に毎回 `make clean` する運用も可能に
- ついでに同日複数のビルドに対応できるようにファイル名にビルド時刻を差し込んでいます

# Contribution

## Issue

- 開放しています。
- こういう機能が欲しいとか書いてもらえると追加したり追加できなかったりします。
- 日本語可。

## Pull Request

- 機能追加や修正は随時受け付けています。
- 私の手元で確認した後でmergeするつもりです。
- コミットメッセージとコメントは日本語で構いません。
    * というかどういう変更なのかちゃんと書いてください…

## Donation

- ~~こんなんに寄付とか正気か？~~
- https://maud.io/ にほしい物リストみたいなリンクはあったと思います

# LICENSE

madoka は [The MIT License](https://github.com/lindwurm/madoka/blob/nextcloud/LICENSE) の下で提供されます。一切の保証はありません。

# Contacts

## lindwurm

- Mastodon: [@hota@mstdn.maud.io](https://mstdn.maud.io/@hota)
- Twitter: [@lindwurm](https://twitter.com/lindwurm)
- GitHub: [@lindwurm](https://github.com/lindwurm)
- Web: [maud.io](https://maud.io)
- Blog: [dev:mordiford](https://dev.maud.io)