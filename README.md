# No-Reference Image Sharpness Measurement Model Based on Edge Width

## 📌 Overview
This repository presents the methodology and empirical results of an academic engineering project developed at Ondokuz Mayıs University. Structured as a formal research paper, the study introduces a user-assisted, content-independent, no-reference sharpness measurement model based on edge width statistics. 

> **Note:** The source code for this project is proprietary and closed-source. This repository serves as a technical overview and showcase of the project's architecture and performance metrics.

## ⚙️ Methodology & Algorithmic Architecture
The software architecture was developed in accordance with object-oriented programming (OOP) principles using **C++17** and integrates **OpenCV 4.8.0** for matrix operations. Memory management is optimized by encapsulating state data to avoid global variables.

Key algorithmic innovations include:
* **Dual-Threshold Interactive Preprocessing:** Overcomes classic hysteresis by implementing a connected-component based dual-threshold architecture. It separates "Main Edge" and "Candidate Edge" pools, allowing user-assisted algorithmic noise filtering via ROI coordinate mapping without permitting random pixel generation.
* **8-Neighborhood Direction Assignment:** Extracts local 3x3 matrices to calculate absolute gray-level differences across vertical, horizontal, and diagonal axes. The orthogonal angle of the minimum gradient variance is assigned as the true edge direction.
* **Slope-Stop Scanning Engine:** Instead of searching for absolute extrema, this algorithm traces the edge profile up to a maximum search limit of 30 pixels. It halts when the instantaneous first derivative meets the predefined slope tolerance (`tolSlope=0.001`) after passing a minimum contrast threshold (`minContrast=0.003`), dynamically locking the edge endpoints.
* **Type 3 Parabolic Distance Weighting:** Measured widths are binned with a sensitivity of 0.375 pixels to find the dominant edge width (w_mp). Step edges are then mathematically weighted using a monotonic Type 3 Parabolic Distance Factor to extract the final objective sharpness score.

## 📊 Performance & Results
Tested on complex textured baselines (e.g., aircraft images with cloud transitions), the model metrics are as follows:
* **Valid Edge Detection Rate:** 96.86%
* **Lost Measurement Ratio:** 3.14%
* **Average Execution Time:** 0.22 seconds per image
* **Near Limit Ratio:** 0.0000 (Zero truncation error during profile scanning)

## 👥 Project Developers
* Duru ÇALIŞKAN
*  Mehmet Emir ÇEBİ
Department of Electrical and Electronics Engineering, Faculty of Engineering, Ondokuz Mayıs University, Samsun, Turkey.
