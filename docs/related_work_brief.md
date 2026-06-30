# Related Work Brief

> 1-page condensed literature synthesis for the WBAN TinyML Fault Detection project.
> Sources: 8 papers spanning 2016–2026 on energy optimization, MAC/PHY modeling,
> ML-based routing, knowledge distillation, and fault detection surveys.

---

The rapid proliferation of Wireless Body Area Networks (WBANs) in healthcare has catalyzed extensive research into two complementary challenges: energy-efficient communication protocols and dependable fault detection. Despite significant progress in both domains, the current body of literature reveals a persistent disconnect between theoretical optimization and real-world edge deployment.

Early efforts in energy optimization focused primarily on refining the IEEE 802.15.6 standard. In 2016, an Enhanced Energy-efficient Channel Access Protocol (EECAP) was proposed to optimize channel access probabilities and frame sizes in Impulse Radio-Ultra Wideband (IR-UWB) networks [1]. While mathematically rigorous, this approach relied exclusively on MATLAB simulations using abstract UWB channel models, with no validation on physical hardware or consideration of body-induced signal attenuation. More recently, Superorthogonal Convolutional Codes (SOCC) were integrated with the IEEE 802.15.6 UWB physical layer to reduce transmission failure ratios [2]. However, this work was similarly confined to simulated AWGN and CM3 multipath environments, neglecting the dynamic MAC layer behaviors that characterize real clinical deployments. In 2023, a two-dimensional Markov chain model was employed to analytically evaluate the effects of payload size and arrival rate on CSMA/CA performance [3]. Though elegant in its mathematical formulation, this approach—validated only through Maple-based analytical solutions—ignores critical real-world phenomena such as hidden terminals, exposed terminals, and channel capture effects that fundamentally alter network behavior at the bedside.

The reliance on simulation-centric validation extends beyond protocol-level studies. In 2024, a genetic fuzzy logic technique (GFuCWO) dynamically adjusted contention window sizes based on traffic conditions [4], yet its evaluation in Castalia/OMNeT++ could not replicate the unpredictable interference patterns of hospital environments. Similarly, a comparative study of IEEE 802.15.6 and LoRaWAN hyper-MAC protocols [5] demonstrated favorable energy metrics in NS3 simulations but explicitly acknowledged its failure to account for body obstruction and electromagnetic interference—factors that dominate real-world WBAN performance.

The emergence of machine learning approaches has introduced new opportunities but also novel limitations. A 2025 study evaluated Decision Trees, K-Nearest Neighbors, Support Vector Machines, and Linear Regression for energy-aware routing [6]. While the methodology represented a shift toward data-driven optimization, the deployment of heavyweight models—particularly SVMs—accelerated rather than mitigated energy depletion on resource-constrained nodes. Furthermore, the reliance on synthetic training data generated from first-order radio models raises concerns about generalization to physical hardware, where algorithmic overhead and memory access patterns significantly impact power consumption.

Recent advances in interpretable machine learning have partially addressed the "black-box" criticism levied against earlier approaches. The Distilled Explanation Model (DEM) framework [7], introduced in 2026, represents a notable step forward by employing knowledge distillation—compressing XGBoost models into transparent Decision Trees—to achieve simultaneous optimization of predictive accuracy and clinical interpretability. Leveraging credible open datasets including MIMIC-IV, eICU, and WESAD, DEM categorizes anomalies into point errors, contextual deviations, and sensor faults. Nevertheless, this framework remains confined to tabular data and does not natively process raw time-series physiological signals or sequential progression patterns. Most critically, despite its focus on anomaly detection in medical IoT contexts, DEM performs no hardware-level energy profiling on physical edge devices, leaving a substantial gap between algorithmic efficacy and deployment feasibility. A concurrent 2026 survey of machine learning methods for fault detection in sensor networks [8] reinforces this observation, noting that existing models frequently prioritize accuracy over interpretability while neglecting energy profiling at the microcontroller level.

## Synthesis and Identified Gap

The literature reveals a clear trajectory from analytical optimization toward data-driven intelligence, yet three fundamental gaps persist across all reviewed works:

1. **Dominance of Simulation:** Nearly all studies depend on simulated environments (MATLAB, NS3, Castalia, Maple) without validation on physical hardware subject to real body obstruction and clinical interference.

2. **No Hardware-Level Energy Profiling:** Energy consumption is estimated through theoretical radio models rather than measured at the MCU level, masking the true cost of algorithm execution.

3. **No Edge Deployment:** Even the most recent interpretable approaches stop short of edge deployment, failing to bridge the chasm between algorithm development and real-time, low-power inference.

## Positioning of This Work

To address these limitations, this work proposes a lightweight edge deployment framework that operates directly on open physiological datasets. Unlike prior approaches that rely on synthetic fault injection or simulated channel conditions, we strictly define faults through three clinically observable phenomena: **excessive packet loss**, **signal distortion**, and **missing data intervals**. Our framework is explicitly optimized for low-power edge hardware, coupling a compact neural architecture with post-training INT8 quantization to ensure sub-100-millisecond inference latency and sub-100-kilobyte memory footprints—constraints that prior works, including the interpretable DEM framework, have not attempted to satisfy.

---

## References

1. **Energy Efficiency Optimization (2016)** — EECAP algorithm, IEEE 802.15.6 IR-UWB. *MATLAB simulation; no hardware validation.*
2. **Toward Dependable IoMT (2022)** — SOCC error correction, IEEE 802.15.6 UWB PHY. *AWGN/CM3 simulation only.*
3. **Effects Investigation of MAC and PHY (2023)** — 2-D Markov chain, CSMA/CA analytical model. *Maple; no real-world validation.*
4. **GFuCWO (2024)** — Genetic fuzzy logic contention window optimization. *Castalia/OMNeT++ simulation.*
5. **IEEE 802.15.6 and LoRaWAN (2024)** — Hyper-MAC comparison (CSMA/CA+TDMA vs ALOHA+TDMA). *NS3 simulation; no body obstruction modeling.*
6. **ML Energy-aware Routing (2025)** — DT, KNN, SVM, LinReg for energy prediction. *Synthetic data; SVM accelerated energy depletion.*
7. **DEM: Distilled Explanation Model (2026)** — Knowledge distillation (XGBoost→DT) for interpretable anomaly detection. *MIMIC-IV, WESAD; no hardware energy profiling.*
8. **ML for Fault Detection Survey (2026)** — Comprehensive survey of ML methods for WSN/WBAN fault detection. *Notes accuracy-over-interpretability trade-off and lack of hardware profiling.*
