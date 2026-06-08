# omni_xpu_kernel Windows Wheels

These are community-built `omni_xpu_kernel` wheels for ComfyUI Windows portable Python 3.13.

They are provided for convenience with the Intel XPU SeedVR2 fork. They are not official Intel builds.

## Install

Install exactly one wheel into the ComfyUI portable Python environment:

```bat
D:\ComfyUI_windows_portable\python_embeded\python.exe -m pip install --force-reinstall --no-deps wheels\ptl_h\omni_xpu_kernel-0.1.0-cp313-cp313-win_amd64.whl
```

Adjust the wheel folder for your GPU.

## Device Targets

| Folder | Intended devices | Build target | SDP preset |
| --- | --- | --- | --- |
| `ptl_h` | Core Ultra Series 3 / Panther Lake, Arc B390/B370 style integrated graphics | `ptl-h` | `SDP_CONFIG_LNL` |
| `xe3_lpg` | Generic Xe3-LPG fallback | `xe3-lpg` | `SDP_CONFIG_LNL` |
| `xe2_lpg` | Core Ultra Series 2 / Lunar Lake and Arrow Lake-H integrated Arc 140V/140T style graphics | `xe2-lpg` | `SDP_CONFIG_LNL` |
| `lnl_m` | Lunar Lake narrow target | `lnl-m` | `SDP_CONFIG_LNL` |
| `bmg` | Discrete Arc B-series / Battlemage | `bmg` | default |

## Notes

- Panther Lake / Arc B390/B370 style integrated GPUs should use `ptl_h`, not `bmg`.
- Arrow Lake-H / Arc 140T should use `xe2_lpg`. The experimental `arl-h` AOT target failed to build locally and is not included.
- Meteor Lake / Core Ultra Series 1 is not included in this wheel set because the local `mtl-h` build did not complete successfully.
- These wheels were built for CPython 3.13 Windows x86_64, matching current ComfyUI Windows portable builds.
- Runtime use does not require installing the full oneAPI compiler toolkit, but the Intel runtime DLLs used by PyTorch XPU / omni_xpu_kernel must be present in the portable Python environment.

