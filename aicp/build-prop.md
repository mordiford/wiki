<!-- TITLE: build.prop -->
<!-- SUBTITLE: ア -->

# build.prop

- `build/tools/buildinfo.sh`
- `system.prop`
- `*.mk:PRODUCT_BUILD_PROP_OVERRIDES`

## ro.build.user が android-build から変えられない？

- AOKPやその派生が源流であるAICPではこのへんでoverrideしてました。クソ。  https://github.com/AICP/vendor_aicp/blob/e7783168ba0d4fce92e3d6022e28f665f30f81af/config/version.mk#L2