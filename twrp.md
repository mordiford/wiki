<!-- TITLE: TWRP -->
<!-- SUBTITLE: TeamWin Recovery Project (TWRP) -->


# CJK対応

ゆーて `ja` と `zh_CN` と `zh_TW` だけなのでCJだね。Kの需要ないのかしら。というのはさておき。

標準ではフォントの容量の都合で削られています。 `BoardConfig.mk` とかに `TW_EXTRA_LANGUAGES := true` を立てましょう。メンテナによっては立ててある。

https://github.com/TeamWin/android_device_oneplus_oneplus3/blob/94923a16a6387eaced38cf4323987b43c9d23412/BoardConfig.mk#L80

# M+ 1mn

Noto Sans CJK JP、プロポーショナルフォントなので各種AAが崩れます。サブセット化したM+ 1mnに変えた例。

patch: https://github.com/mordiford/bootable_recovery/commit/1c49b28642eb4e0f523e453b874d4e49371f0042


# build

これがべんり

[minimal-manifest-twrp/platform_manifest_twrp_omni: Limited manifest for building TWRP](https://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni)

## local_manifests

oneplus3の場合。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <remove-project name="android_bootable_recovery" />
  <project name="mordiford/bootable_recovery" path="bootable/recovery" remote="github" revision="o8.1" />

  <project name="TeamWin/android_device_oneplus_oneplus3" path="device/oneplus/oneplus3" remote="github" revision="android-8.1" />
</manifest>
```