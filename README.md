# BF F405 穿越机飞控

基于 STM32F405 的穿越机飞控开发资料，包含电路设计预览、Betaflight 配置、CLI 备份、历史固件及调试记录。

本项目在开发过程中参考借鉴了 **Omnibus F4V3** 飞控设计，相关电路工程、BOM 和说明资料保存在 `references/omnibus-f4v3/`。

当前资料来自开发阶段归档，硬件版本、配置文件和固件的对应关系仍在整理中。

## 资料组成

| 部分 | 内容 |
|---|---|
| 本项目电路预览 | 2 张 PCB 图片、2 张原理图图片 |
| 板级配置 | 自定义配置及 AIRB、CYCL、DAKE 等参考配置 |
| CLI 备份 | 原始调试备份，包含资源映射、外设和运行参数 |
| 历史固件 | 原资料中 STM32F405 的 4 个版本 HEX |
| 调试记录 | USB 连接等开发问题记录 |
| 参考设计 | Omnibus F4V3 的电路工程、BOM、图片、PDF、器件手册及历史固件 |

## 目录结构

```text
.
├── README.md
├── .gitignore
├── hardware/
│   └── previews/                  原理图和 PCB 预览
├── configs/
│   ├── targets/                   目标定义片段
│   ├── cli/                       自定义 CLI 配置草稿
│   ├── reference/                 参考板卡配置
│   └── snapshots/                 原始调试备份
├── firmware/
│   └── prebuilt/                  历史 HEX 及说明
├── docs/
│   ├── development/               开发问题记录
│   └── tools.md                   原归档中的工具和驱动清单
└── references/
    ├── README.md                  参考来源与整理说明
    └── omnibus-f4v3/              Omnibus F4V3 参考设计
```

## 电路资料

本项目现有的电路预览位于 [hardware/previews/](hardware/previews/)，包括：

- `2D_PCB12_2026-10-16.png`
- `2D_PCB14_2026-10-16.png`
- `SCH_Schematic5_1-P1_2026-10-16.png`
- `SCH_Schematic5_3-P3_2026-10-16.png`

这几张图片对应的可编辑工程和硬件版本需要补充确认。参考目录中的 Omnibus 工程单独作为参考设计保存。

当前归档未提供可明确对应本项目硬件版本的完整制造导出包，后续将补充可编辑电路工程、BOM、Gerber 和钻孔文件。

## 配置文件

| 目录 | 文件 | 用途与状态 |
|---|---|---|
| [targets/](configs/targets/) | `配置文件子版.config` | 含 `#pragma once`、`#define` 的目标定义片段，使用入口待说明 |
| [cli/](configs/cli/) | `配置文件母版.config` | 含 `board_name`、`resource` 等命令的配置草稿，适用版本待核对 |
| [reference/](configs/reference/) | AIRB、CYCL、DAKE 配置 | 参考板卡的配置资料 |
| [snapshots/](configs/snapshots/) | 原始 CLI 备份 | 保留开发时的资源映射与参数快照 |

这些文件的语法和用途不同，应结合对应的 Betaflight 版本使用。原始 CLI 备份中包含 `NO CONFIG FOUND` 提示以及 `HEX6X` 混控和调试参数，尚未整理为本项目的推荐配置。

## 固件资料

[firmware/prebuilt/](firmware/prebuilt/) 保存原始 `Official Firmware/` 目录中的以下文件：

- `betaflight_4.4.0_STM32F405.hex`
- `betaflight_4.4.1_STM32F405.hex`
- `betaflight_4.5.0_STM32F405.hex`
- `betaflight_4.5.1_STM32F405.hex`

这些文件作为历史归档原样保留；下载来源、对应硬件和配置组合仍需补充验证。当前资料未包含完整的 Betaflight 固件源码及构建流程。

Omnibus 原资料中的 3.5.7、4.1.1 固件随参考设计单独保存，详见 [参考资料说明](references/README.md)。

## 参考设计：Omnibus F4V3

本项目参考借鉴了 Omnibus F4V3 飞控设计，资料位于 [references/omnibus-f4v3/](references/omnibus-f4v3/)。

其中包含：

- `F4.pcb`、`F4.Sch`、`F4.pro` 电路工程文件
- BOM、元件位置图和板卡正反面图片
- 原理图和 PCB PDF
- MPU-6000、MPU-9250 器件手册
- 原资料中的历史固件
- 原始 README 和 LICENSE

阅读入口：

- [参考资料来源与整理说明](references/README.md)
- [Omnibus F4V3 原始 README](references/omnibus-f4v3/README.md)
- [原资料附带的 LICENSE](references/omnibus-f4v3/LICENSE)

原资料保留一份 PCB 工程作为入口。内容不同的历史原理图仍保存在原始 BF F405.zip 中，尚未进行 CAD 差异比对。原始项目地址、作者信息以及本项目具体借鉴的模块待补充。

## 调试与工具

- USB 连接等开发问题记录见 [docs/development/](docs/development/)。
- 原归档中的配置软件、驱动版本和文件清单见 [docs/tools.md](docs/tools.md)。

大型安装包和驱动仍保留在原始 BF F405.zip 中。上述开发记录和历史软件版本未经本次整理重新验证。

