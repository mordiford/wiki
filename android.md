<!-- TITLE: Android -->
<!-- SUBTITLE: Safer, smarter, more powerful & sweeter than ever.-->

# メモ

## ビルドベンチマーク奴

- 参考: [XDA PC Hardware Analysis : Intel Core X and AMD Threadripper Face Off](https://www.xda-developers.com/test-ryzen-intel-amd-core-x-threadripper/)
- Google Pixel XL (`marlin`) 向けに LineageOS 14.1 をビルドする
- LOSのソースは2017-12-28 13:30頃の時点のもの
- local_manifests は以下

```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <project name="LineageOS/android_device_google_marlin" path="device/google/marlin" />
  <project name="LineageOS/android_kernel_google_marlin" path="kernel/google/marlin" />

  <project name="LineageOS/android_device_qcom_common" path="device/qcom/common" />
  <project name="LineageOS/android_packages_resources_devicesettings" path="packages/resources/devicesettings" />

  <project name="LineageOS/android_vendor_nxp-nfc_opensource_frameworks" path="vendor/nxp-nfc/opensource/frameworks" />
  <project name="LineageOS/android_vendor_nxp-nfc_opensource_libnfc-nci" path="vendor/nxp-nfc/opensource/libnfc-nci" />
  <project name="LineageOS/android_vendor_nxp-nfc_opensource_Nfc" path="vendor/nxp-nfc/opensource/Nfc" />

  <project name="TheMuppets/proprietary_vendor_google" path="vendor/google" />
</manifest>
```


### スペック

| part | id | spec | manufacturer |
|:----:|:-------------:|:-----------------------:|:------------:|
| CPU | Core i7-2600K | 3.40GHz, 4C/8T | Intel |
| RAM | W3U1600PS-8G | 32GB (8GBx4), DDR3-1600 | Panram |
| SSD0 | TS512GSSD370S | 512GB, SATA3(6Gbps) | Transcend |
| SSD1 | MZ-75E500B | 500GB, SATA3 (6Gbps) | Samsung |

ビルド用のディレクトリは SSD1 に作ってるけど、 `/tmp` はブート用のSSD0を指してるかも。

### 結果

- 初回（ccacheは有効にしたけど空）

<iframe src="https://mstdn.maud.io/@mashiro/99250503901299675/embed" class="mastodon-embed" style="max-width: 100%; border: 0" height="200" width="600"></iframe><script src="https://mstdn.maud.io/embed.js" async="async"></script>

- 2回目、ccache有り（初回のキャッシュが効く）

<iframe src="https://mstdn.maud.io/@mashiro/99250818017265250/embed" class="mastodon-embed" style="max-width: 100%; border: 0" height="200" width="600"></iframe><script src="https://mstdn.maud.io/embed.js" async="async"></script>