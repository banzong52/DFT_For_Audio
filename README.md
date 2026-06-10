# DFT_For_Audio

基于 DFT（离散傅里叶变换）的音频降噪、加密与解密实验。

## 文件说明

| 文件 | 内容 |
|------|------|
| `DFT.ipynb` | 主程序：余弦低通滤波降噪 + FFT 频域加密/解密，批量处理 |
| `Draw.ipynb` | DFT 时频域对比演示 |

## 功能

### 1. 音频降噪
- 余弦锥形过渡带低通滤波器，避免吉布斯振铃
- 传递函数：

$$H(f)=\begin{cases}1,& f\le f_c\\\frac{1}{2}\left(1+\cos\left(\pi\frac{f-f_c}{W}\right)\right),& f_c<f\le f_c+W\\0,& f>f_c+W\end{cases}$$

### 2. 频域加密/解密
- 正频率复数置换 + 相位旋转
- 基于 `rfft`/`irfft`，自动保持共轭对称，解密误差 ~10⁻¹⁵

## 使用

1. 将 `.wav` 文件放入 `data/` 目录
2. 运行 `DFT.ipynb` 全部单元格
3. 结果输出到 `output/<文件名>/` 目录

## 环境

- Python 3.12+
- numpy, scipy, matplotlib
