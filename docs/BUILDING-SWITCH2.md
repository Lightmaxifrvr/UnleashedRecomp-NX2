# Building for Nintendo Switch 2

The Switch 2 build uses `devkitA64` for the compiler and
[libnx-ounce](https://github.com/alula/libnx-ounce) for the Switch 2 runtime.
Install libnx-ounce into the devkitPro tree so it provides
`$DEVKITPRO/libounce`, including `switch.specs`, headers, and `lib/libnx.a`.

Build and install OunceVK's Switch 2 portlib into
`$DEVKITPRO/portlibs/switch2` first. The package must contain
`lib/libvulkan.a` and `include/vulkan/`.

```sh
export DEVKITPRO=/c/devkitPro
export SWITCH_PLATFORM=ounce
export NVK_ROOT=/c/devkitPro/portlibs/switch2
export CLANG64=/c/devkitPro/msys2/clang64/bin
export SWITCH_NXLINK=1
tools/build-switch.sh
```
