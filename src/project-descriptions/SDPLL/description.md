# 基于带宽自适应的半数字锁相环设计

## 🚀 项目概述

本项目设计并实现了一种基于 22nm FDSOI 工艺的**半数字锁相环（SDPLL）**。  
该架构通过去除时间数字转换器（TDC），并引入分离的比例路径与积分路径，实现高带宽与低抖动性能。

本设计重点优化：

- 不同 PVT 条件下的环路带宽稳定性  
- 系统锁定鲁棒性  
- 相位噪声与抖动性能  

---

<p class="text-xs text-gray-400 mb-2 uppercase tracking-wide">关键词</p>

<div class="flex flex-wrap gap-2">
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">SDPLL</span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">锁相环</span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">22nm FDSOI</span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">带宽自适应</span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">低抖动</span>
</div>

---

## 🧩 系统架构

该 SDPLL 主要由以下模块组成：

- 相位频率检测器（PFD）  
- 比例路径（Proportional Path）  
- 积分路径（用于生成多个离散控制电压）  
- 压控振荡器（VCO）  
- 可编程分频器  
- 初始化机制（用于预设 VCO 工作频率以加快锁定过程）  

<div class="text-center mt-6">
  <img src="./picture/1.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    所提出的 SDPLL 系统架构
  </p>
</div>

与传统 CPPLL 相比，本设计：

- 去除环路滤波电阻 → 无额外极点  
- 无需 TDC → 降低复杂度与功耗  
- 采用直接电压注入 → 提高环路响应速度  

---

## 🔬 关键设计技术

### 无电阻比例路径

- 消除热噪声  
- 减小环路延迟  
- 提高环路带宽  

---

### 带宽自适应机制

为实现不同 PVT 条件下的带宽稳定性：

- 利用激活的 Vint 节点数量作为 PVT 状态指示  
- 动态调整比例路径电容  

<div class="text-center mt-6">
  <img src="./picture/2.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    基于 Vint 激活状态的带宽自适应机制
  </p>
</div>

结果：

<p class="text-center font-medium mt-2">
  f<sub>ref</sub> / f<sub>BW</sub> ≈ 4–6
</p>

---

### 分频器鲁棒性优化

在慢角（SS）条件下，由于传播延迟增加，分频器可能出现不稳定。

解决方法：

- 引入基于 INITB 的初始化机制  
- 确保系统启动时进入有效状态  

---

### VCO 余量优化

通过优化晶体管尺寸，提高：

- 最大振荡频率  
- 调谐范围与频率余量  

---

## 📊 实验结果

主要性能指标如下：

- 输出频率：5 GHz  
- 参考频率：500 MHz  
- RMS 抖动：约 250 fs  
- 功耗：约 4 mW  

<div class="text-center mt-6">
  <img src="./picture/3.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    原始与优化后 PLL 在不同工艺角下的相位噪声对比
  </p>
</div>

<div class="text-center mt-6">
  <img src="./picture/4.png" class="rounded-xl shadow-lg mx-auto" />
</div>

---

## 🧾 总结

本项目提出了一种无需 TDC 的 SDPLL 架构，实现了：

- 高环路带宽  
- 低抖动性能  
- 良好的 PVT 鲁棒性  

所提出的带宽自适应机制有效稳定了环路行为，使该设计适用于高速时钟生成系统。