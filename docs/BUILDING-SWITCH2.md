# Building for Nintendo Switch 2

The Switch 2 build uses `devkitA64` for the compiler and
[libnx-ounce](https://github.com/alula/libnx-ounce) for the Switch 2 runtime.
Install libnx-ounce into the devkitPro tree so it provides
`$DEVKITPRO/libounce`, including `switch.specs`, headers, and `lib/libnx.a`.

Build and install OunceVK's Switch 2 portlib into
`$DEVKITPRO/portlibs/switch2` first. The package must contain
`lib/libvulkan.a` and `include/vulkan/`.

```sh
export DEVKITPRO=/opt/devkitpro
export NVK_ROOT=/path/to/ouncevk
export SWITCH_PLATFORM=ounce
tools/build-switch.sh
```

`NVK_ROOT` should point directly to the packaged `portlibs/switch2` directory.

`SWITCH_PLATFORM=switch` remains the default and uses the original libnx
runtime. The Ounce toolchain selects the Switch 2 CPU flags and defines
`__SWITCH2__`; the application and SDL2 link against the `libnx-ounce`
runtime without changing the existing Switch 1 path.
