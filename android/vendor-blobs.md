<!-- TITLE: Vendor Blobs -->
<!-- SUBTITLE: Working with proprietary blobs -->

# 参考

[Working with proprietary blobs | LineageOS Wiki](https://wiki.lineageos.org/proprietary_blobs.html)

# 概要

実機で動作するAndroid OSのビルドにおいて避けては通れない、プロプライエタリなブロブについて

## 流れ

- `${ANDROID_ROOT}/device/${VENDOR}/${DEVICE}/` 以下に `proprietary-files.txt` を持つ。
	- これ書くのが一番厳しいのでは（移植マンではないのでなんもわからん）
		- わたしも書き方知りたい
	- 書き方は参考のLineageOS Wikiや構成が近い他機種覗くと良いのかもしれない
- `extract-files.sh` と `setup-makefiles.sh` は `vendor/cm/build/template/` から （15.0 以降では `/vendor/lineage/build/template`）コピーして `DEVICE` と `VENDOR` を記入する
- 端末を接続してadbが通る状態にしておく
- `extract-files.sh` を実行する
	- いきなりAICPとかの派生ROMでやってるとたぶん `vendor/cm` が見つからないと思うので `HELPER` のパスをちゃんと変えておきたい
		- そもそも移植やろうとしてるときにあんまり余計な要素挟まないほうがいいのはそれはそうで、LOSでやるべき
- いい感じに `${ANDROID_ROOT}/vendor/${VENDOR}/${DEVICE}/` 以下に配置される（はず）

## おまけ

block-based OTA(zipの中身に `/system` とかがなくて `system.new.dat` みたいになってるやつ)が有効なLineageOSのzipから `sdat2img` 使ってブロブ取り出す方法。
やったことはあるけど知見まとめてなかったらいつの間にかwikiにも載ってたね。

[Extracting proprietary blobs from LineageOS zip files](https://wiki.lineageos.org/extracting_blobs_from_zips.html)

NexusとかのFactory Imageをマウントして取り出すみたいなのは https://dev.maud.io/entry/2016/12/28/howto-build-lineageos-14/ の途中でさらっと書いた気がします。

結局 `proprietary-files.txt` がキモなのには変わりないので頑張っていきましょう。