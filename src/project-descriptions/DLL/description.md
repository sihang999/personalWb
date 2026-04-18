# DLL：电路设计、版图实现与后仿验证

## 🚀 项目概述

本项目基于 22nm FDSOI 工艺，实现了一个 **延迟锁定环（Delay-Locked Loop, DLL）** 的完整设计流程，涵盖从**电路设计到版图实现以及后仿验证**。

主要工作包括：

- 电路级设计与分析  
- 使用 Cadence Virtuoso 进行版图设计  
- 物理验证（DRC / LVS）  
- 寄生参数提取后的后仿真  

项目目标是实现 **精确的时钟对齐、稳定的锁定行为以及最小化版图寄生带来的性能影响**。

---

<p class="text-xs text-gray-500 mb-2 uppercase tracking-wide">关键词：</p>

<div class="flex flex-wrap gap-2">
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">
    延迟锁定环（DLL）
  </span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">
    相位检测器
  </span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">
    压控延迟线（VCDL）
  </span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">
    电荷泵
  </span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">
    后仿真
  </span>
</div>

---

## 🧩 系统结构

DLL 由三个主要功能模块组成：

- 采样信号生成模块  
- 采样保持电路  
- 压控延迟线（VCDL）  

整体构成一个 **一阶闭环系统**，具有良好的稳定性和快速锁定能力。

<div class="text-center mt-6">
  <img src="./picture/Figure 1.1.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    图 1.1：延迟锁定环（DLL）的系统框图
  </p>
</div>

---

## ⚙️ 核心模块

### 采样信号生成

通过 NAND 和 NOR 逻辑门生成脉冲信号：

- 上升沿 → SAMPLE  
- 下降沿 → SAMPLE2  

<div class="text-center mt-6">
  <img src="./picture/Figure 3.1.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    图 3.1：基于 NAND 门的采样信号生成电路
  </p>
</div>

<div class="text-center mt-6">
  <img src="./picture/Figure 3.2.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    图 3.2：基于 NOR 门的采样信号生成电路
  </p>
</div>

---

### 采样保持模块

该模块集成了：

- 相位检测  
- 电荷泵行为  
- 低通滤波  

用于生成控制电压：

- VCONT  
- VCONT_N  

<div class="text-center mt-6">
  <img src="./picture/Figure 3.5.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    图 3.5：采样保持电路结构
  </p>
</div>

---

### 压控延迟线（VCDL）

VCDL 是实现延迟调节的核心模块：

- 差分结构  
- 单调延迟调节特性  
- 稳定的相位控制能力  

<div class="text-center mt-6">
  <img src="./picture/Figure 3.9.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    图 3.9：差分结构的 VCDL 单元电路
  </p>
</div>

---

## 🧠 工作原理

DLL 通过迭代调节延迟实现锁定：

1. 检测相位差  
2. 调整控制电压  
3. 通过 VCDL 调节延迟  
4. 达到相位锁定  

在稳态条件下：

- 每级延迟 ≈ **1/8 T**  
- 总延迟 ≈ **1/2 T**  

<div class="text-center mt-6">
  <img src="./picture/Figure 3.14.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    图 3.14：延迟调节过程的波形示意
  </p>
</div>

---

## 🖥️ 版图实现

版图设计的关键策略包括：

- 器件对称布局  
- 降低寄生效应  
- 提高面积利用效率  

<div class="text-center mt-6">
  <img src="./picture/Figure 3.17.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    图 3.17：优化后的 DLL 最终版图
  </p>
</div>

---

## 📊 实验结果

后仿结果表明：

- 延迟误差：**0.5 ps – 3.5 ps**  
- 锁定速度略快于原理图仿真  
- 各级延迟稳定一致  

<div class="text-center mt-6">
  <img src="./picture/Figure 4.1.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    图 4.1：后仿波形结果，展示稳定的延迟行为
  </p>
</div>

<div class="text-center mt-6">
  <img src="./picture/Figure 4.2.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    图 4.2：原理图与后仿延迟结果对比
  </p>
</div>

---

## 🧾 总结

本项目完成了从电路设计到版图实现再到后仿验证的完整混合信号 IC 设计流程。

实验结果表明：

- 延迟误差控制在 **0.5–3.5 ps** 范围内  
- 每级延迟约为 **1/8T**，总延迟约为 **1/2T**  
- 系统在后仿条件下能够稳定锁定  

整体设计验证了该 DLL 结构在高性能时钟系统中的稳定性与可靠性。