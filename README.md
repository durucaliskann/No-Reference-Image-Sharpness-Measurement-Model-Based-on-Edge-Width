# No-Reference-Image-Sharpness-Measurement-Model-Based-on-Edge-Width
An academic engineering project introducing a user-assisted, no-reference image sharpness measurement model based on edge width statistics using C++ and OpenCV.
# No-Reference Image Sharpness Measurement Model Based on Edge Width

## 📌 Overview
This repository presents the methodology and empirical results of an academic engineering project developed at Ondokuz Mayıs University[cite: 1]. The study, structured as a formal research paper, introduces a user-assisted, content-independent, no-reference sharpness measurement model based on edge width statistics[cite: 1]. 

> **Note:** The source code for this project is proprietary and closed-source. This repository serves as a technical overview and showcase of the project's architecture and performance metrics.

## ⚙️ Methodology & Technologies
The software architecture was developed in accordance with object-oriented programming (OOP) principles using **C++17**, and integrated with the **OpenCV 4.8.0** computer vision library for matrix operations[cite: 1]. 

Key architectural innovations include:
* **Dual-Threshold Interactive Canny:** Overcoming classic hysteresis thresholding by developing a connected component-based dual-threshold interactive preprocessing architecture that separates "Main Edge" and "Candidate Edge" pools[cite: 1].
* **Slope-Stop Scanning Engine:** Instead of searching for absolute endpoints, a Slope-Stop scanning algorithm was designed to track the instantaneous derivative of the gray level profile, maximizing edge measurement precision[cite: 1].
* **Weighting:** Outputs are weighted using a parabolic Type 3 distance factor to emphasize step edges that reflect blur[cite: 1].

## 📊 Performance & Results
The model was rigorously tested, yielding highly stable results demonstrating potential for real-time industrial quality control:
* **Valid Edge Detection Rate:** 96.86%[cite: 1].
* **Lost Measurement Ratio:** Reduced to 3.14%[cite: 1].
* **Average Execution Time:** 0.22 seconds per image[cite: 1].
* **Near Limit Ratio:** 0.0000 (Proving the algorithm does not artificially truncate natural edge transitions)[cite: 1].

## 👥 Project Developers
* Mehmet Emir ÇEBİ[cite: 1]
* Duru ÇALIŞKAN[cite: 1]
Department of Electrical and Electronics Engineering, Faculty of Engineering, Ondokuz Mayıs University, Samsun, Turkey[cite: 1].
