---
title: cuda
description: 
published: true
date: 2024-11-30T03:02:57.054Z
tags: c++
editor: markdown
dateCreated: 2024-05-23T02:51:48.314Z
---

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
1. dst（目标地址）
- 指定拷贝的目标地址，可以是主机或设备上的内存地址，取决于 kind 的设置。

2. dpitch（目标行间距）
- 指定目标内存的行间距（以字节为单位）。
- 它是目标地址中相邻两行数据的起始地址之间的距离。如果目标数据是一个二维数组，dpitch 应该等于该数组的实际行大小。

3. src（源地址）
指定拷贝的源地址，可以是主机或设备上的内存地址，取决于 kind 的设置。

4. spitch（源行间距）
- 指定源内存的行间距（以字节为单位）。
- 它是源地址中相邻两行数据的起始地址之间的距离。如果源数据是一个二维数组，spitch 应该等于该数组的实际行大小。

5. width（拷贝宽度）
- 指定拷贝的宽度（以字节为单位）。
- 它是每行中实际要拷贝的数据宽度，不需要等于 spitch 或 dpitch。

6. height（拷贝高度）
- 指定拷贝的行数，即二维区域的高度。
- 这决定了要拷贝的行数。

7. kind（拷贝类型）
- 指定拷贝的方向。可能的值包括：
cudaMemcpyHostToHost：主机到主机的拷贝。
cudaMemcpyHostToDevice：主机到设备的拷贝。
cudaMemcpyDeviceToHost：设备到主机的拷贝。
cudaMemcpyDeviceToDevice：设备到设备的拷贝。

8. stream（CUDA 流）
- 指定用于异步操作的 CUDA 流。
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