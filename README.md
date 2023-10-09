# rocm

## Supported Cards

For these models of GPUs use the ROCm OpenCL stack is supported.

Name                        |     Architecture    |    LLVM Target
------                      |       ------        |     ------
AMD Radeon™ RX 7900 XTX     |      RDNA3          |    gfx1100
AMD Radeon™ RX 7900 XT      |      RDNA3          |    gfx1100
AMD Radeon™ RX 7600         |      RDNA3          |    gfx1102
AMD Radeon™ RX 7600         |      RDNA2          |    gfx1030
AMD Radeon™ RX 7600         |      RDNA2          |    gfx1030
AMD Radeon™ RX 6800 XT      |      RDNA2          |    gfx1030
AMD Radeon™ RX 6800         |      RDNA2          |    gfx1030
AMD Radeon™ RX 6750         |      RDNA2          |    gfx1032
AMD Radeon™ RX 6700 XT      |      RDNA2          |    gfx1032
AMD Radeon™ RX 6700         |      RDNA2          |    gfx1032
AMD Radeon™ RX 6650 XT      |      RDNA2          |    gfx1032
AMD Radeon™ RX 6600 XT      |      RDNA2          |    gfx1032
AMD Radeon™ RX 6600         |      RDNA2          |    gfx1032
AMD Radeon Pro™ W7900       |      RDNA3          |    gfx1100
AMD Radeon Pro™ W7800       |      RDNA3          |    gfx1100
AMD Radeon Pro™ W6800       |      RDNA2          |    gfx1030
AMD Radeon Pro™ W6600       |      RDNA2          |    gfx1032
AMD Radeon Pro™ W5500       |      RDNA1          |    gfx1012
AMD Radeon Pro™ VII         |      GCN5.1         |    gfx906

https://rocmdocs.amd.com/en/latest/release/windows_support.html#windows-supported-gpus

Legacy OpenCL stack (Proprietary), supports legacy products older than Vega 10 (opencl-amdgpu-pro and lib32-opencl-amdgpu-pro) (https://github.com/archdevlab/amdgpu-pro.git).

ROCm OpenCL stack, supports Vega 10 and later products (this repo).
