# Building for Nintendo Switch 2

The Switch 2 build uses `devkitA64` for the compiler and
[libnx-ounce](https://github.com/alula/libnx-ounce) for the Switch 2 runtime.
Install libnx-ounce into the devkitPro tree so it provides
`$DEVKITPRO/libounce`, including `switch.specs`, headers, and `lib/libnx.a`.

The existing Switch build inputs and Mesa/NVK driver are still required:

```sh
export DEVKITPRO=/opt/devkitpro
export NVK_ROOT=/path/to/mesa-switch
export SWITCH_PLATFORM=ounce
tools/build-switch.sh
```

`SWITCH_PLATFORM=switch` remains the default and uses the original libnx
runtime. The Ounce toolchain selects the Switch 2 CPU flags and defines
`__SWITCH2__`; the application and SDL2 link against the `libnx-ounce`
runtime without changing the existing Switch 1 path.
