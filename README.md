# 🚗 Distracted Driver Detection with Deep Learning Networks (State Farm Distracted Driver Detection)

<div align="center">

[![Aparat Pitch Video](https://img.shields.io/badge/Aparat-Product_Pitch-ec1b24?style=for-the-badge&logo=aparat)](https://www.aparat.com/v/dzq86t9)
[![YouTube Pitch Video](https://img.shields.io/badge/YouTube-Product_Pitch-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://youtu.be/81qpQSVFSF0?si=VR1zr5mQt1Sc-Do9)
[![Project Report](https://img.shields.io/badge/Google_Drive-Project_Report-1FA463?style=for-the-badge&logo=googledrive&logoColor=white)](https://drive.google.com/file/d/1n0Htn8fYO4Xi63GhZazjSBeCDGAtRvAx/view)

</div>

---

## 📌 Project Overview
This project was designed and implemented as a final assignment for the **Machine Learning** course. The primary objective is to develop an intelligent system capable of automatically detecting and classifying drivers' distracted behaviors and states based on deep learning and computer vision algorithms.

Utilizing the valid **State Farm Distracted Driver Detection** image dataset, driver behaviors are categorized into 10 distinct classes:
- `c0`: Safe driving
- `c1`: Texting - right
- `c2`: Talking on the phone - right
- `c3`: Texting - left
- `c4`: Talking on the phone - left
- `c5`: Operating the radio
- `c6`: Drinking
- `c7`: Reaching behind
- `c8`: Hair and makeup
- `c9`: Talking to passenger

---

## 🧠 Architectures & Strategies
To achieve maximum accuracy and provide a comprehensive performance comparison, the **Transfer Learning** technique was employed on two prominent architectures:

1. **ResNet50:** A deep model with 50 layers and Residual Connections designed to extract complex visual features and attain the highest classification accuracy.
2. **MobileNetV2:** An optimized model featuring Depthwise Separable Convolutions, tailored for environments with limited computational resources and Edge Devices.

### 💡 Technical Insights and Implementation Strategies:
- 🛡️ **Preventing Data Leakage:** The separation of training and validation data based on the 'Driver ID' was conducted using `GroupShuffleSplit`. This ensures that drivers present in the validation set remain completely unseen during the training phase.
- 🔄 **Targeted Augmentation:** Horizontal mirroring (`horizontal_flip=False`) was intentionally omitted to preserve the semantic distinction between classes involving the left and right hands.
- 🚀 **Two-Phase Fine-Tuning:**
  - **Phase 1:** Freezing the network's base layers and training only the final classification layers.
  - **Phase 2:** Unfreezing the top base layers and performing fine-tuning with a very low learning rate (`lr = 1e-5`).

---

## 📂 Repository Structure
This repository is organized in accordance with Clean Architecture principles as follows:

```text
📦 MachineLearning-2026-Project-DistractedDriver
 ┣ 📂 code/               # Python source code, data pipeline, and model implementations
 ┣ 📂 docs/               # Final PDF report and LaTeX source codes
 ┣ 📂 media/              # Evaluation plots, confusion matrix, and HTML presentation file
 ┣ 📂 data/               # Dataset retrieval guide (files are excluded due to large size)
 ┣ 📜 .gitignore          # File for excluding heavy and temporary files
 ┣ 📜 requirements.txt    # List of required Python libraries
 ┗ 📜 README.md           # Main documentation and project identity
