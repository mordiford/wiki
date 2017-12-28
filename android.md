<!-- TITLE: Android -->
<!-- SUBTITLE: Safer, smarter, more powerful & sweeter than ever.-->

# メモ

## ビルドベンチマーク奴

### スペック

| part | id | spec | manufacturer |
|:----:|:-------------:|:-----------------------:|:------------:|
| CPU | Core i7-2600K | 3.40GHz, 4C/8T | Intel |
| RAM | W3U1600PS-8G | 32GB (8GBx4), DDR3-1600 | Panram |
| SSD0 | TS512GSSD370S | 512GB, SATA3(6Gbps) | Transcend |
| SSD1 | MZ-75E500B | 500GB, SATA3 (6Gbps) | Samsung |

### 結果

- ccache無し

<iframe src="https://mstdn.maud.io/@mashiro/99250503901299675/embed" class="mastodon-embed" style="max-width: 100%; border: 0" width="400"></iframe><script src="https://mstdn.maud.io/embed.js" async="async"></script>

- ccache有り (`prebuilts/misc/linux-x86/ccache/ccache -M 30G`)

<iframe src="https://mstdn.maud.io/@mashiro/99250818017265250/embed" class="mastodon-embed" style="max-width: 100%; border: 0" width="400"></iframe><script src="https://mstdn.maud.io/embed.js" async="async"></script>