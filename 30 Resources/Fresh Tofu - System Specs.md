# Fresh Tofu - System Specs

*Hostname: fresh-tofu*
*Last updated: 2026-02-12*

## Overview

| Item | Details |
|------|---------|
| **OS** | Arch Linux (kernel 6.18.7-arch1-1) |
| **Architecture** | x86_64 |
| **Uptime** | 8h 53m (at time of documentation) |

## CPU

| Item | Details |
|------|---------|
| **Model** | AMD Ryzen 9 5900HX with Radeon Graphics |
| **Cores** | 8 cores / 16 threads |
| **Architecture** | x86_64, 2 threads per core |
| **NUMA** | 1 node (0-15) |
| **Current Scaling** | 67% |

## GPU

| Item | Details |
|------|---------|
| **Model** | AMD Cezanne [Radeon Vega Series / Radeon Vega Mobile Series] |
| **Vendor** | AMD/ATI (Device ID: 1002:1638) |
| **Subsystem** | ASUSTeK Computer Inc. (Device ID: 1043:1f6c) |
| **Driver** | amdgpu |
| **Vulkan Support** | ✅ Yes (Vulkan Instance Version: 1.4.335) |
| **VRAM** | Integrated (shares system RAM) |

## Memory

| Item | Details |
|------|---------|
| **Total RAM** | 15 GiB |
| **Used** | 6.9 GiB |
| **Free** | 5.5 GiB |
| **Available** | 8.2 GiB |
| **Swap** | 7.5 GiB (3.4 GiB used, 4.1 GiB free) |
| **Swap Type** | zram (compressed RAM-based swap) |

## Storage

| Item | Details |
|------|---------|
| **Drive** | WD PC SN530 / SanDisk Ultra 3D NVMe SSD |
| **Model** | SN530 / Blue SN550 (DRAM-less) |
| **Interface** | NVMe (PCIe 3.0) |
| **Total Size** | 476.9 GiB |
| **Used** | 116 GiB (25%) |
| **Available** | 357 GiB (75%) |
| **Partition Layout** | LUKS encrypted root + 2 GiB boot |

### Filesystem

| Mount Point | Size | Used | Avail | Use% |
|-------------|------|------|-------|------|
| `/` (root)   | 475G | 116G | 357G | 25% |
| `/boot`      | 2.0G | 201M | 1.9G | 10% |
| `/home`      | 475G | 116G | 357G | 25% |

## AI/ML Capabilities

### Current Setup
- **voxtype**: Whisper (ggml-small, 487 MB) with Vulkan GPU acceleration
- **Model location**: `/home/tofu/.local/share/voxtype/models/ggml-small.bin`
- **GPU Backend**: Vulkan (AMD Radeon Graphics)
- **VRAM Usage**: ~823 MB during inference (model + working buffers)

### Potential Additions
| Tool | Model Size | VRAM Impact | Notes |
|------|------------|-------------|-------|
| **Coqui XTTS v2** | 2-3 GB | ~3.5 GB total | Expressive TTS, emotion support |
| **Combined (Whisper + XTTS)** | - | ~4.3 GB total | Fits within 8 GB VRAM |

## System Load

| Metric | Current |
|--------|---------|
| **Load Average (1m)** | 2.15 |
| **Load Average (5m)** | 5.10 |
| **Load Average (15m)** | 6.25 |
| **Active Users** | 1 |

## Notes

- System runs well for AI workloads with Vulkan GPU acceleration
- Ample storage available (357 GB free)
- 8 GB integrated GPU VRAM sufficient for both Whisper and XTTS
- zram swap provides fast, compressed swap without disk wear
- LUKS encrypted root filesystem for security

---

*Documented by Bean (Tofurkybot Bean) — Andrew's digital assistant* 🗿
