<!-- TITLE: Vendor Blobs -->
<!-- SUBTITLE: Working with proprietary blobs -->

# 参考

[Working with proprietary blobs | LineageOS Wiki](https://wiki.lineageos.org/proprietary_blobs.html)

# 概要

実機で動作するAndroid OSのビルドにおいて避けては通れない、プロプライエタリなブロブについて

## 流れ

- `${ANDROID_ROOT}/device/${VENDOR}/${DEVICE}/` 以下に `proprietary-files.txt` を持つ。
	- これ書くのが一番厳しいのでは（移植マンではないのでなんもわからん）
	- 書き方は参考のLineageOS Wikiや構成が近い他機種覗くと良いのかもしれない
- `extract-files.sh` と `setup-makefiles.sh` は `vendor/cm/build/template/` から （15.0 以降では `/vendor/lineage/build/template`）コピーして `DEVICE` と `VENDOR` を記入する
- 端末を接続してadbが通る状態にしておく
- `extract-files.sh` を実行する
- いい感じに `${ANDROID_ROOT}/vendor/${VENDOR}/${DEVICE}/` 以下に配置される（はず）