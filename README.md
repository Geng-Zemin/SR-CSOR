# SR-CSOR

**Structure Reliability-Driven Compact Second-Order Orientation Representation for Optical–SAR Image Matching**

[中文](#中文说明) | [English](#english)

---

## 中文说明

### 项目简介

SR-CSOR 是一种面向光学与合成孔径雷达（SAR）影像局部匹配的方法。该方法利用紧凑的双通道方向结构表征描述局部轴向结构，并结合方向相干性与结构能量对方向响应进行可靠性调制。加权后的两个方向分量被编码为复数结构场，通过联合频域相关估计局部位移，最后利用几何一致性筛选获得可靠匹配点。

本仓库提供 SR-CSOR 的 Windows 可执行程序。当前公开版本仅包含编译后的程序和使用说明，不包含 MATLAB 源代码。

### 文件说明

```text
SR-CSOR/
├─ SR_CSOR.exe    # Windows可执行程序
└─ README.md      # 中英文使用说明
```

### 运行环境

- 64位 Windows 10 或 Windows 11；
- MATLAB Runtime R2023a（9.14）。

如果计算机尚未安装对应版本的 MATLAB Runtime，请先从 MathWorks 官方网站下载安装。运行本程序不需要完整 MATLAB，也不需要 MATLAB 许可证。

### 使用方法

1. 下载 `SR_CSOR.exe`；
2. 确认已经安装 MATLAB Runtime R2023a；
3. 双击运行 `SR_CSOR.exe`；
4. 在界面中依次选择原始影像、参考影像和输出文件夹；
5. 点击运行按钮执行匹配。

首次启动时，MATLAB Runtime 的初始化可能需要一定时间。

### 输入要求

- 输入为一对光学–SAR影像；
- 两幅影像应具有相同的宽度与高度；
- 两幅影像之间应具有初始位置先验；
- 当前版本主要面向有限搜索范围内的局部平移匹配；
- 支持 MATLAB `imread` 可读取的常见影像格式，例如 PNG、JPG、TIF 和 BMP。

### 输出结果

程序将在所选输出文件夹中生成：

- `SR_CSOR_matching_lines.png`：匹配点连线图；
- `SR_CSOR_checkerboard.png`：配准棋盘格图；
- `SR_CSOR_matching_points.txt`：匹配点坐标文件。

TXT 文件每行包含四列：

```text
original_x  original_y  reference_x  reference_y
```

坐标采用 MATLAB 图像坐标约定，其中 `x` 表示列坐标，`y` 表示行坐标。

### 默认参数

当前发布程序采用论文实验中的统一配置：

- 模板尺寸参数：100 pixels；
- 搜索范围参数：50 pixels；
- 几何一致性剔除阈值：1.5 pixels；
- 最大候选点数量：200。

### 适用范围与限制

SR-CSOR 主要用于具有初始位置先验的局部光学–SAR平移匹配。当前版本不专门处理大幅旋转、显著尺度变化、强透视畸变或局部非刚性形变。弱纹理、大面积均匀区域以及真实位移超出搜索范围时，匹配性能可能下降。

### 引用

如果该程序对您的研究有帮助，请引用 SR-CSOR 论文：

> Zemin Geng, Bo Yang, Jiajia Li, Yongkang Mei, Taiping Wang, Yaxin Dong. *SR-CSOR: Structure Reliability-Driven Compact Second-Order Orientation Representation for Optical–SAR Image Matching*. Manuscript under preparation.

论文正式发表后，本条目将补充期刊、年份和 DOI 信息。

---

## English

### Overview

SR-CSOR is designed for local matching between optical and synthetic aperture radar (SAR) images. It represents local axial structures using a compact two-channel directional representation and modulates directional responses using local directional coherence and structural energy. The weighted components are encoded into a complex-valued structural field, local displacements are estimated through joint frequency-domain correlation, and unreliable correspondences are removed using geometric-consistency filtering.

This repository provides the compiled Windows application of SR-CSOR. The current public release contains only the executable and documentation; MATLAB source code is not included.

### Repository Contents

```text
SR-CSOR/
├─ SR_CSOR.exe    # Windows executable
└─ README.md      # Chinese and English documentation
```

### Requirements

- 64-bit Windows 10 or Windows 11;
- MATLAB Runtime R2023a (9.14).

If the required MATLAB Runtime is not installed, download it from the official MathWorks website before running the application. A full MATLAB installation and MATLAB license are not required.

### Usage

1. Download `SR_CSOR.exe`;
2. Confirm that MATLAB Runtime R2023a is installed;
3. Run `SR_CSOR.exe`;
4. Select the original image, reference image, and output folder in the GUI;
5. Click the run button to start matching.

The first launch may take longer while MATLAB Runtime is initialized.

### Input Requirements

- The input is an optical–SAR image pair;
- The two images must have the same width and height;
- An initial positional prior between the images is required;
- The current release is intended primarily for local translation matching within a limited search range;
- Common image formats supported by MATLAB `imread`, including PNG, JPG, TIF, and BMP, can be used.

### Outputs

The selected output folder will contain:

- `SR_CSOR_matching_lines.png`: correspondence visualization;
- `SR_CSOR_checkerboard.png`: registration checkerboard;
- `SR_CSOR_matching_points.txt`: matched point coordinates.

Each row of the TXT file contains four columns:

```text
original_x  original_y  reference_x  reference_y
```

Coordinates follow the MATLAB image convention: `x` is the column coordinate and `y` is the row coordinate.

### Default Parameters

The released application uses the unified configuration adopted in the paper:

- Template-size parameter: 100 pixels;
- Search-range parameter: 50 pixels;
- Geometric-consistency rejection threshold: 1.5 pixels;
- Maximum number of candidate points: 200.

### Scope and Limitations

SR-CSOR is primarily intended for local optical–SAR translation matching with an initial positional prior. The current release is not specifically designed for large rotations, substantial scale changes, strong perspective distortion, or local non-rigid deformation. Performance may decrease in weakly textured or homogeneous regions, or when the true displacement exceeds the configured search range.

### Citation

If this software is useful in your research, please cite the SR-CSOR paper:

> Zemin Geng, Bo Yang, Jiajia Li, Yongkang Mei, Taiping Wang, Yaxin Dong. *SR-CSOR: Structure Reliability-Driven Compact Second-Order Orientation Representation for Optical–SAR Image Matching*. Manuscript under preparation.

Journal, year, and DOI information will be added after publication.
