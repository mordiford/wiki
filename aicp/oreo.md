<!-- TITLE: Oreo -->
<!-- SUBTITLE: AICP-o-13.x -->

# AICP-mordiford

[![](https://lindwurm.neocities.org/img/discord_banner_mini.png)](https://bit.ly/hellolineage)

* Japanese

## 注意事項

> 動作に関して**一切の保証はありません**。
> 導入により、**端末の文鎮化**、SDカードの破損、核戦争の勃発、アラームが正常に鳴動せず会社をクビになる、などの事態を招いても、私たちが**責任を負うことはありません**。
> このROMに含まれる機能についての懸念がある場合は、導入前に**きちんと調べる**ことを強く推奨します。
> **あなた**はこれらの危険を伴う改変を行うことを自ら**選択しました**。端末を台無しにしたとして、私たちを指差し罵るならば、私たちはきっとあなたのことを笑うでしょう。
{.is-danger}


## 方針

- [公式Nightly Build](http://dwnld.aicp-rom.com/) が存在している機種は原則として私の手元にあるもの以外対応しない
- 対応機種は [mordiford/IceManifest:oreo](https://github.com/mordiford/IceManifests/projects/2) で管理する

## 特徴

- `android-8.1.0_r1`
    - セキュリティパッチレベル: `2017-12-05`
- 以下に挙げるアプリは無い
    - apps/
			- Calendar
		      - 私がGoogleカレンダーとか使うので
			- Eleven
			    - 私はGPM使ってるので
			- AICP_OTA
			    - 公式以外想定されてないので
- AICPと相容れなかった要素についての謎改変。
	- [packages_apps_AicpExtras](https://github.com/mordiford/packages_apps_AicpExtras)
- 最新のビルドはたぶんSlimOTAが通知します
	- なおデータの更新は手動

## 更新履歴

- `設定` → `AICP Extra` → `更新履歴` でビルド時点での更新履歴が出ますのでご活用ください

## インストール方法

1. 推奨されているFWを焼く
2. 推奨されているTWRPを焼く
    - [https://twrp.me/Devices/](https://twrp.me/Devices/) から見つけるかxdaとかで探しましょう
3. もしもに備えてバックアップを取る
4. `/system`, `/data`, `/cache`, `Dalvik/ART Cache` を Wipe する
5. ROM, GApps, なんかその他を焼く
6. Reboot to System
7. Enjoy.

## ダウンロード

- [Downloads](/aicp/oreo/downloads) を参照のこと。
- 動作報告がなければ廃止するし、あれば継続します。
	- DL数把握してないので。

## サンクス

敬称略。

### ソースコード/翻訳

- [AICP](https://github.com/AICP)
- [LineageOS](https://github.com/LineageOS)
- [Crowdin/AICP Translators](https://crowdin.com/project/aicp)
- 以上に対する貢献者と各デバイス向けリポジトリの貢献者各位

### 機材提供

- SHIMADA Hirofumi / [@dejiko](https://github.com/dejiko)
- [SAKURA Internet Inc.](https://www.sakura.ad.jp/)

## 連絡先

### hota

- Web: https://maud.io
- Mastodon: https://mstdn.maud.io/@hota
- Twitter: https://twitter.com/lindwurm
- GitHub: https://github.com/lindwurm
    - org: https://github.com/mordiford
- GitLab: https://gitlab.com/lindwurm
- xda: http://forum.xda-developers.com/member.php?u=6024671
- Donation: http://bit.ly/hotalist