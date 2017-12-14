<!-- TITLE: nougat -->
<!-- SUBTITLE: AICP-n-12.1 -->

# AICP-mordiford

[![](https://lindwurm.neocities.org/img/discord_banner_mini.png)](https://bit.ly/hellolineage)

* Japanese

## 注意事項

> /* テンプレ
>  
> - 動作に関して**一切の保証はありません**
> - 導入により、**端末の文鎮化**、SDカードの破損、核戦争の勃発、アラームが正常に鳴動せず会社をクビになる、などの事態を招いても、私たちが**責任を負うことはありません**
> - このROMに含まれる機能についての懸念がある場合は、導入前に**きちんと調べる**ことを強く推奨します
> - **あなた**はこれらの危険を伴う改変を行うことを自ら**選択しました**。端末を台無しにしたとして、私たちを指差し罵るならば、私たちはきっとあなたのことを笑うでしょう
>  
> ここまでテンプレ */

- **非公式版です**
    - わたしは毎日は更新しないはずなので、公式のNightlyビルドが欲しかったら http://dwnld.aicp-rom.com/ へどうぞ
- AICPでサポートされている機種の場合であっても、公式ビルドとの互換性はだいたい無いです。
    - 違うリポジトリからの派生で独自にAICP対応してるので…
    - 公式ビルドからの**上書きインストールによる移行は非推奨**とし、バグ報告は**受理しません**
- **持っていない機種向けへの対応は、単なるユーザではなくテスターとして協力していただくことを前提としています**
    - 持ってない以上、何が動いて何が動いてないかは分からない部分が多いので動作報告は積極的に投げてください
    - 動作等の報告が一切無い機種は需要がないと判断し、最悪の場合提供を打ち切ることがあります
    - 大きめの変更が入ると、何かを犠牲にしながら何かの改善が行われたり行われなかったりします
    - 報告が直接飛んでこない問題は一生直しようがないので、一人で愚痴る暇があったら報告を投げてください
- 起動しなくても笑って許してkernelだけ焼き直すとか、自分なりに試してくれるとこっちでの原因の切り分けが一段階楽になります。無理にとは言わないが
- 不具合は(できれば)[gist](https://gist.github.com/)か[pastebin](https://pastebin.com/)か[hastebin](https://www.hastebin.com/)あたりにログ貼ってきてくれると助かります
- 基本Twitterか[Mastodon](https://github.com/lindwurm/mastodon/wiki/Accounts)、メールは返信遅め
- ターゲットの追加予定は https://github.com/mordiford/IceManifests/projects/1 で

## 特徴

- `android-7.1.2_r36`
    - セキュリティパッチレベル: `2017-12-05`
- KRACK, Blueborne対応済
- 一部機種のkernel: cpufreq_alucard の追加
    - 快適な動作とそこそこなバッテリ持ちを両立できる、一押しのCPUガバナ
- 以下に挙げる一部のアプリが含まれていません
    - apps/
        - Calendar
            - Googleカレンダーとか使うでしょどうせ
        - Eleven
            - お好みの音楽プレイヤーあるでしょ皆さん
            - わたしは [Shuttle+](https://play.google.com/store/apps/details?id=com.simplecity.amp_pro) とかGPMとか
        - AICP_OTA
            - 公式以外想定されてないのでもう最初から外した
                - OFFICIALじゃないとビルドされないようになってるけどね…
- AICP本家に取り込まれる前の翻訳テスト版。
    - [frameworks_base](https://github.com/mordiford/frameworks_base)
    - [packages_apps_AicpExtras](https://github.com/mordiford/packages_apps_AicpExtras)
- SlimOTAによる新着ビルド通知を始めました
    - 普通に焼いてもらうけどね
- **[Magisk](https://forum.xda-developers.com/apps/magisk/official-magisk-v7-universal-systemless-t3473445)** がAICP本家に入りましたがrevertしています
    - 嫌いではないんだけどデフォルトにすることに疑念が有るので。
        - 詳細は https://dev.maud.io/entry/2017/04/07/i-dont-like-embed-magisk
    - ~~SafetyNetなにそれおいしいの？~~
    - root/suの導入は各自でお好みのを入れてください
    - というかkernelに手を入れてたりするのであんまりSafetyNet/CTS周りは保証できないです…
        - あとSafetyNet/CTS通して使いたい人はEnforcing推奨

## 更新履歴

- `設定` → `AICP Extra` → `更新履歴` でビルド時点での更新履歴が出ますのでご活用ください

## インストール方法

### 初回のクリーンインストール、所謂 Clean Flash

1. ファームウェアを推奨されているバージョンに揃える
    - ここ合ってないとインストールできないこと多いです
2. 最新のTWRPを焼く
    - [https://twrp.me/Devices/](https://twrp.me/Devices/) から見つけるかxdaとかで探しましょう
3. 必要に応じてバックアップを取る
    - もしものための。
4. `/system`, `/data`, `/cache`, `Dalvik/ART Cache` を Wipe する
    - 内部ストレージとmicroSD以外がまっさらになります
5. ROMを焼く
6. GAppsを焼く
    - 個人的にはOpenGAppsのnanoかpicoあたりが推奨
7. その他を焼く
    - カスタムカーネルなりMagiskなりSUなり[Koruri-Installer](https://androplus.org/Entry/3501/)なり
8. 再起動
    - 正常に起動できなかったらつらい
9. Enjoy.

### 更新時の上書きインストール、所謂 Dirty Flash

1. 必要に応じてバックアップを取る
    - もしものための。
2. ROMを焼く
3. GAppsを焼く
    - アップデート時はいるとかいらないとか言われるけどわたしは焼く派
4. その他を焼く
    - カスタムカーネルなりMagiskなりSUなりKoruri-Installerなり
5. `Dalvik/ART Cache` を Wipe する
    - だいじ
6. 再起動
    - 正常に起動できなかったらつらい
7. Enjoy.

## ダウンロード

- [Downloads](/aicp/nougat/downloads) を参照のこと。
- 追加・廃止は動作報告の届き具合とかで需要を見て判断します。
- 廃止はアナウンスしたあとでも必要があれば覆せるので要望と動作報告は投げて欲しいです
    - 正確なユーザ数把握してません

## サンクス（敬称略）

### ソースコード

- [AICP](https://github.com/AICP)
- [LineageOS](https://github.com/LineageOS)
- 以上に対する貢献者と各デバイス向けリポジトリの貢献者各位

### 翻訳協力

- [Crowdin/AICP Translators](https://crowdin.com/project/aicp)
- [Transifex/AICP-ja team](https://www.transifex.com/lindwurm/aicp-ja/)
    - Izumi Inami / [@droidfivex](https://github.com/droidfivex)
    - Sarisia / [@a1ces](https://github.com/a1ces)
    - hanpen / [@hanpen914](https://github.com/hnpn914)
    - AndroPlus / [@AndroPlus-org](https://github.com/AndroPlus-org)

### 機材提供

- SHIMADA Hirofumi / [@dejiko](https://github.com/dejiko)
- [SAKURA Internet Inc.](https://www.sakura.ad.jp/) / [@sakura-internet](https://github.com/sakura-internet)

## Author

### lindwurm / ほた

- Web: https://maud.io
    - Wishlistのリンクあり
- Twitter: https://twitter.com/lindwurm
    - たぶん窓口。日本語でおｋ
- Mastodon: https://mstdn.maud.io/@hota
    - 最近はこっちが活発。
    - メンテ時は[ここ](/mastodon/accounts)参照
- GitHub: https://github.com/lindwurm
    - org: https://github.com/mordiford
        - こっちがAndroid方面の拠点
- GitLab: https://gitlab.com/lindwurm
    - ときどき
- xda: http://forum.xda-developers.com/member.php?u=6024671
    - 頻度低め
- 寄付: GitHubのプロフィールに書いてるメールアドレス宛にAmazonギフト券とか頂けると今後も活動を継続していく支えになります