<!-- TITLE: Vendor Blobs -->
<!-- SUBTITLE: Working with proprietary blobs -->

# 参考

https://wiki.lineageos.org/proprietary_blobs.html

# 概要

実機で動作するAndroid OSのビルドにおいて避けては通れない、プロプライエタリなブロブについて

## 流れ

- ${ANDROID_ROOT}/device/${VENDOR}/${DEVICE}/ 以下に `proprietary-files.txt` を持つ。
- `extract-files.sh` と `setup-makefiles.sh` は `vendor/cm/build/template/` から （15.0 以降では `/vendor/lineage/build/template`）コピーして `DEVICE` と `VENDOR` を記入する。