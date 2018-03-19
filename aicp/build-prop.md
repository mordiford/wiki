<!-- TITLE: build.prop -->
<!-- SUBTITLE: ア -->

# build.prop

- `build/tools/buildinfo.sh`
- `system.prop`
- `*.mk:PRODUCT_BUILD_PROP_OVERRIDES`

# ro.build.user が android-build から変えられない？

- AOKPやその派生が源流であるAICPではこのへんでoverrideしてました。クソ。  https://github.com/AICP/vendor_aicp/blob/e7783168ba0d4fce92e3d6022e28f665f30f81af/config/version.mk#L2
- `sed 's/android-build/lindwurm/g' vendor/aicp/config/version.mk` しても途中で上書きされてて意味なかった（これはどこから？）ので、`vendor_aicp/config/version.mk` のoverrideを消すcommitを入れるしかなさそう。
	- 入れた https://github.com/mordiford/vendor_aicp/commit/869d6743b6bd7594d0578c800d6664df16d2882a

```diff
- PRODUCT_BUILD_PROP_OVERRIDES += BUILD_VERSION_TAGS=release-keys USER=android-build BUILD_UTC_DATE=$(shell date +"%s")
+ PRODUCT_BUILD_PROP_OVERRIDES += BUILD_VERSION_TAGS=release-keys BUILD_UTC_DATE=$(shell date +"%s")
```

- これで普通にビルドしてるユーザを指すようになった。
- `release-keys` はともかく `android-build` に固定する理由とは…

## 試行錯誤録

トゥート: https://mstdn.maud.io/@hota/99706238626603169


- `ro.build.user` でLOSのorg内を検索する
- `build/tools/buildinfo.sh` にそれっぽいのがある

```sh
echo "ro.build.user=$USER"
```

- 上書きしてみるが反映されない
	- そもそも `$USER` が反映されずに `android-build` になってるのなんなん…？
- 一旦ビルドが通って `out` が残っている環境で `out/target/product/${device}/obj/ETC/system_build_prop_intermediates` だけ飛ばして上のやつを書き換えると一応そこだけ再ビルドされて反映されるらしい
	- make clean する運用では無意味
- ビルド途中で上書きされているっぽい
	- 「後から上書きされている」で閃いたので `PRODUCT_BUILD_PROP_OVERRIDES` の線を疑う
- `USER=android-build` をGitHub全体で検索する
	- AOKPのリポジトリが出てくる
- `common_version.mk` みたいなとこにあったのでAICPでも `vendor/aicp/config/version.mk` を疑う
- 1行目に見つかる

```mk
PRODUCT_BUILD_PROP_OVERRIDES += BUILD_VERSION_TAGS=release-keys USER=android-build BUILD_UTC_DATE=$(shell date +"%s")
```