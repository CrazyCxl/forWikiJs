---
title: cuda
description: 
published: true
date: 2025-02-10T09:02:34.439Z
tags: c++
editor: markdown
dateCreated: 2024-05-23T02:51:48.314Z
---

# 工具
## 性能分析
nvvp.exe

### linux
可以在linux里生成在windows上查看
#### Nsight Compute (ncu / ncu-ui / nv-nsight-cu-cli / nv-nsight-cu-ui)

用途：针对 GPU 内核级别的性能分析，收集详细的硬件计数器、资源利用率、内核执行统计数据等。
使用方式：
命令行：使用 ncu 或 nv-nsight-cu-cli 来运行分析，例如：
```bash
ncu --target-processes all ./your_cuda_app
```
图形界面：使用 ncu-ui 或 nv-nsight-cu（通常为 nv-nsight-cu 的符号链接）启动 GUI 分析工具。
#### Nsight Systems (nsys / nsight-sys / nsys-ui)

用途：面向系统级别的性能分析，适合分析 CPU 与 GPU、OS 调度、内存传输、线程同步等全局运行情况。
使用方式：
命令行：
```bash
nsys profile -o my_profile ./your_cuda_app
```
图形界面：生成的分析文件可以用 nsys-ui 打开，进行详细的时序分析和瓶颈定位。
#### nvprof / nvvp (Visual Profiler)

用途：传统的 CUDA 命令行和图形界面性能分析工具，用于测量 GPU 内核执行时间、内存拷贝带宽等。
注意：从 CUDA 11.x 开始，nvprof 和 nvvp 已经逐步被 Nsight Compute 和 Nsight Systems 所取代，未来可能会逐步淘汰。

# 库
thrust 数学库

# 计算方法
规约计算

# 函数说明
## cudaMemcpy2DAsync 
```
cudaError_t cudaMemcpy2DAsync(
    void* dst,            // 目标地址
    size_t dpitch,        // 目标地址的行间距
    const void* src,      // 源地址
    size_t spitch,        // 源地址的行间距
    size_t width,         // 拷贝数据的宽度（字节）
    size_t height,        // 拷贝数据的高度（行数）
    cudaMemcpyKind kind,  // 拷贝类型
    cudaStream_t stream   // CUDA 流（异步）
);
```
### 参数说明
- ```dst```（目标地址）
 指定拷贝的目标地址，可以是主机或设备上的内存地址，取决于 kind 的设置。

- ```dpitch```（目标行间距）
 指定目标内存的行间距（以字节为单位）。
 它是目标地址中相邻两行数据的起始地址之间的距离。如果目标数据是一个二维数组，dpitch 应该等于该数组的实际行大小。

- ```src```（源地址）
指定拷贝的源地址，可以是主机或设备上的内存地址，取决于 kind 的设置。

- ```spitch```（源行间距）
 指定源内存的行间距（以字节为单位）。
 它是源地址中相邻两行数据的起始地址之间的距离。如果源数据是一个二维数组，spitch 应该等于该数组的实际行大小。

- ```width```（拷贝宽度）
 指定拷贝的宽度（以字节为单位）。
 它是每行中实际要拷贝的数据宽度，不需要等于 spitch 或 dpitch。

- ```height```（拷贝高度）
 指定拷贝的行数，即二维区域的高度。
 这决定了要拷贝的行数。

- ```kind```（拷贝类型）
 指定拷贝的方向。可能的值包括：
cudaMemcpyHostToHost：主机到主机的拷贝。
cudaMemcpyHostToDevice：主机到设备的拷贝。
cudaMemcpyDeviceToHost：设备到主机的拷贝。
cudaMemcpyDeviceToDevice：设备到设备的拷贝。

- ```stream```（CUDA 流）
 指定用于异步操作的 CUDA 流。
如果为 0，拷贝操作将在默认流中执行。

## cufftPlanMany
```
cufftHandle plan;
int rank = 1;  // 1D transform
int n[] = {131072};  // Size of each dimension
int inembed[] = {0};  // Input data storage dimensions (NULL in this case)
int istride = 1;  // Distance between successive input elements
int fftlen = 131072;  // FFT length
int overlap = 39321;  // Overlap length
int idist = fftlen - overlap;  // Distance between the first element of two consecutive signals in a batch of the input data
int onembed[] = {0};  // Output data storage dimensions (NULL in this case)
int ostride = 1;  // Distance between successive output elements
int odist = fftlen/2;  // Distance between the first element of two consecutive signals in a batch of the output data for CUFFT_R2C
int batch = 7;  // Batch size for this transform

cufftPlanMany(&plan, rank, n, inembed, istride, idist, onembed, ostride, odist, CUFFT_R2C, batch);
```
参数说明
- ```plan```
指向 FFT 计划的句柄（cufftHandle），用于后续执行 FFT。

- ```rank```
变换的维度数（即几维 FFT，例如：1D、2D、3D）。

- ```n```
指向包含每个维度大小的数组。例如，rank = 2 时，n = {width, height} 表示二维大小。

- ```inembed```
输入数据的每个维度的嵌入大小，通常设置为 NULL 表示不使用嵌入大小。

- ```istride```
输入数组中连续元素的步幅（stride），一般为 1。

- ```idist```
每个批次输入数据之间的距离。例如，设置为每个 FFT 输入的起始位置偏移。

- ```onembed```
输出数据的每个维度的嵌入大小，通常也设置为 NULL。

- ```ostride```
输出数组中连续元素的步幅。

- ```odist```
每个批次输出数据之间的距离。

- ```type```
FFT 的类型，支持以下类型：
CUFFT_R2C: 实数到复数的 FFT。
CUFFT_C2R: 复数到实数的逆 FFT。
CUFFT_C2C: 复数到复数的 FFT。
CUFFT_D2Z: 双精度实数到复数。
CUFFT_Z2D: 双精度复数到实数。
CUFFT_Z2Z: 双精度复数到复数。

- ```batch```
批量执行 FFT 的次数。