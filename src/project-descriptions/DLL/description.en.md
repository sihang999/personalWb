# DLL: Circuit Design, Layout and Post-Layout Verification

## 🚀 Overview

This project presents the complete implementation of a **Delay-Locked Loop (DLL)** in 22nm FDSOI technology, covering the full design flow from **circuit design to layout implementation and post-layout verification**.

The work includes:
- Circuit-level design and analysis
- Layout design using Cadence Virtuoso  
- Physical verification (DRC/LVS)  
- Post-layout simulation with parasitic extraction  

The objective is to achieve **accurate timing alignment, stable locking behavior, and minimal layout-induced degradation**.

---

<p class="text-xs text-gray-500 mb-2 uppercase tracking-wide">Keywords:</p>

<div class="flex flex-wrap gap-2">
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">
    Delay-Locked Loop(DLL)
  </span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">
    Phase Detector
  </span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">
    Voltage-Controlled Delay Line(VCDL)
  </span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">
    Charge Pump
  </span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">
    Post-Layout Simulation
  </span>
</div>

---

## 🧩 System Design

The DLL is composed of three main functional blocks:

- Sample Signal Generation  
- Sample-and-Hold Circuit  
- Voltage-Controlled Delay Line (VCDL)  

Together, they form a **first-order closed-loop system** with strong stability and fast locking capability.

<div class="text-center mt-6">
  <img src="./picture/Figure 1.1.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    Block diagram of the Delay-Locked Loop (DLL)
  </p>
</div>

---

## ⚙️ Core Modules

### Sample Signal Generation

Pulse signals are generated using NAND and NOR logic:

- Rising edge → SAMPLE  
- Falling edge → SAMPLE2  

<div class="text-center mt-6">
  <img src="./picture/Figure 3.1.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    Sample signal generation using NAND gate
  </p>
</div>

<div class="text-center mt-6">
  <img src="./picture/Figure 3.2.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    Sample signal generation using NOR gate
  </p>
</div>

---

### Sample-and-Hold

This block integrates:
- Phase detection  
- Charge pump behavior  
- Low-pass filtering  

It produces control voltages:

- VCONT  
- VCONT_N  

<div class="text-center mt-6">
  <img src="./picture/Figure 3.5.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    Sample-and-hold circuit structure
  </p>
</div>

---

### Voltage-Controlled Delay Line (VCDL)

The VCDL is the core component responsible for delay tuning:

- Differential architecture  
- Monotonic delay control  
- Stable phase adjustment  

<div class="text-center mt-6">
  <img src="./picture/Figure 3.9.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    Differential VCDL cell structure
  </p>
</div>

---

## 🧠 Working Principle

The DLL operates through iterative delay tuning:

1. Detect phase difference  
2. Adjust control voltages  
3. Tune delay via VCDL  
4. Reach phase lock  

At steady state:

- Each stage delay ≈ **1/8 T**  
- Total delay ≈ **1/2 T**  

<div class="text-center mt-6">
  <img src="./picture/Figure 3.14.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    Waveform illustration of delay tuning process
  </p>
</div>

---

## 🖥️ Layout Implementation

Key layout strategies include:

- Symmetrical transistor placement  
- Parasitic minimization  
- Area-efficient design  

<div class="text-center mt-6">
  <img src="./picture/Figure 3.17.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    Final DLL layout with optimized symmetry and routing
  </p>
</div>

---

## 📊 Results

Post-layout simulation confirms:

- Delay deviation: **0.5 ps – 3.5 ps**  
- Slightly faster locking than schematic  
- Stable operation across all delay stages  

<div class="text-center mt-6">
  <img src="./picture/Figure 4.1.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    Post-layout simulation waveforms showing stable delay behavior
  </p>
</div>

<div class="text-center mt-6">
  <img src="./picture/Figure 4.2.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    Comparison between schematic and post-layout delay results
  </p>
</div>

---

## 🧾 Conclusion

This project demonstrates a complete mixed-signal IC design flow, from circuit-level understanding to layout implementation and post-layout verification.

The results confirm that:
- The DLL achieves accurate delay control with deviation within **0.5–3.5 ps**
- Each stage introduces a delay of approximately **1/8T**, achieving **1/2T total delay**
- The system maintains stable locking behavior under post-layout conditions

Overall, the design validates the robustness and reliability of the DLL architecture for high-performance timing applications.