# Semi-Digital Phase-Locked Loop Design with Bandwidth Tracking

## 🚀 Overview

This project presents the design of a **Semi-Digital Phase-Locked Loop (SDPLL)** implemented in 22nm FDSOI technology.  
The proposed architecture eliminates the need for a Time-to-Digital Converter (TDC) and introduces separate proportional and integral control paths to achieve high bandwidth and low jitter performance.

The design focuses on improving:

- Loop bandwidth stability across PVT conditions  
- Locking robustness  
- Phase noise and jitter performance  

---

<p class="text-xs text-gray-400 mb-2 uppercase tracking-wide">Keywords</p>

<div class="flex flex-wrap gap-2">
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">SDPLL</span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">Phase-Locked Loop</span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">22nm FDSOI</span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">Bandwidth Tracking</span>
  <span class="px-2 py-1 text-sm bg-gray-100 dark:bg-gray-800 rounded-md border border-gray-200 dark:border-gray-700">Low Jitter</span>
</div>

---

## 🧩 Architecture

The SDPLL consists of the following main components:

- Phase Frequency Detector (PFD)  
- Proportional Path  
- Integral Path (generating multiple discrete control voltages)  
- Voltage-Controlled Oscillator (VCO)  
- Programmable Divider  
- Initialization mechanism for VCO frequency to accelerate locking  

<div class="text-center mt-6">
  <img src="./picture/1.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    Proposed SDPLL architecture
  </p>
</div>

Unlike conventional CPPLL, this design:

- Removes the loop filter resistor → no additional pole  
- Eliminates the TDC → reduced complexity and power consumption  
- Uses direct voltage injection → faster loop response  

---

## 🔬 Key Design Techniques

### Resistor-Free Proportional Path

- Eliminates thermal noise  
- Reduces loop delay  
- Enables higher loop bandwidth  

---

### Bandwidth Tracking Mechanism

To stabilize loop bandwidth across PVT conditions:

- The number of active Vint nodes is used as a PVT indicator  
- The proportional path capacitance is dynamically adjusted accordingly  

<div class="text-center mt-6">
  <img src="./picture/2.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    Bandwidth tracking mechanism based on Vint activation
  </p>
</div>

Result:

<p class="text-center font-medium mt-2">
  f<sub>ref</sub> / f<sub>BW</sub> ≈ 4–6
</p>

---

### Divider Robustness Improvement

At slow corners, increased propagation delay may lead to instability in the divider.

Solution:

- Introduce an INITB-assisted initialization mechanism  
- Ensure a valid startup state for reliable operation  

---

### VCO Headroom Optimization

Transistor sizing is optimized to improve:

- Maximum oscillation frequency  
- Tuning range and headroom  

---

## 📊 Results

Performance summary:

- Output frequency: 5 GHz  
- Reference frequency: 500 MHz  
- RMS jitter: ~250 fs  
- Power consumption: ~4 mW  

<div class="text-center mt-6">
  <img src="./picture/3.png" class="rounded-xl shadow-lg mx-auto" />
  <p class="text-sm text-gray-500 dark:text-gray-400 mt-2">
    Phase noise comparison of the original and optimized PLL across corners.
  </p>
</div>

<div class="text-center mt-6">
  <img src="./picture/4.png" class="rounded-xl shadow-lg mx-auto" />
</div>

---

## 🧾 Conclusion

This project demonstrates a TDC-free SDPLL architecture with:

- High loop bandwidth  
- Low jitter performance  
- Strong robustness across PVT conditions  

The proposed bandwidth tracking mechanism effectively stabilizes loop behavior, making the design suitable for high-speed clock generation systems.