# FT_Transformer_DDOS

# DDoS Attack Prediction Using FT-Transformer

This repository contains the code, experiments, and analysis from my Undergraduate Thesis, which investigates the application of the **FT-Transformer** model for predicting DDoS attacks using continuous tabular data.

## 📌 Objective
The goal of this project was to evaluate the effectiveness of **FT-Transformer** in detecting DDoS attacks across different datasets, exploring its generalization capability and interpretability.

## 📂 Repository Structure
```
📦 TCC-FTTransformer
├── 📁 data                # Datasets used in experiments
├── 📁 notebooks           # Jupyter Notebooks with analyses and experiments
├── 📁 models              # Trained models and checkpoints
├── 📁 results             # Experiment results
├── 📄 requirements.txt    # Required dependencies
├── 📄 README.md           # Project guide
└── 📄 main.py             # Main script for training and evaluation
```

## 🔧 Environment Setup

For the environment setup you have to strictly follow this guide https://github.com/yandex-research/rtdl-revisiting-models?tab=readme-ov-file#setup-the-environment made by the original author of the FT-Transformer 
  
## ⚠️ Warning about CPU usage

If your dataset is heavy, your computer will struggle to run the code, and it will probably run out of video memory, which was my case. So you will have to upload the repository to Google Colab and use one of their more powerful machines.

The configuration for running the experiments used the T4 machine provided by Google Colab. This machine was chosen due to its configuration, which offers a balance between performance and cost, and is suitable for the model's requirements. The T4 has a 2.20 GHz Intel Xeon processor, 16 GB of RAM and an NVIDIA Tesla T4 GPU, which has 16 GB of GDDR6 video memory.

## 📊 Datasets Used
- **CTU-13**: Used in the initial testing phase.
- **CICDDoS2019**: Employed to validate the model’s robustness in varied scenarios.
- **Generalization between captures**: Experiments were conducted by training on one dataset and validating on another to assess the model’s performance in unknown attack scenarios.

## 🧪 Methodology
1. **Data Preprocessing**:
   - Normalization and handling of missing values.
   - Selection of key features for binary classification (attack/non-attack).

2. **Model Training**:
   - Utilization of **FT-Transformer** for supervised learning.
   - Hyperparameter tuning for improved performance.

3. **Tested Approaches**:
   - Linear classifier at the Transformer output.
   - Application of **Sigmoid** function for better score interpretation.
   - Testing a **MLP** at the output to enhance final decision-making.

4. **Results Evaluation**:
   - Metrics used: **AUC-ROC, F1-score, Precision, and Recall**.
   - Performance comparison by varying training and testing datasets.

## 📈 Key Findings
- **FT-Transformer** proved effective in predicting DDoS attacks, especially in controlled environments.
- Generalization between different dataset captures presented challenges, highlighting the need for more data to improve model robustness.
- The **Sigmoid function** improved the interpretability of the linear classifier scores.
- Using a **MLP** at the output provided marginal gains but added complexity to the model.

## 🚀 Running Experiments
1. To train the model with capture 51 from **CTU-13**:
   ```bash
   python main.py --dataset CTU-51 --train
   ```
2. To test a trained model on another dataset:
   ```bash
   python main.py --dataset CICDDoS2019 --test --checkpoint models/ft_transformer_ctu51.pth
   ```
3. To visualize results:
   ```bash
   python evaluate.py
   ```

## 📌 Conclusion
This project demonstrated the potential of FT-Transformer for DDoS attack prediction but also highlighted the importance of diverse datasets and additional techniques to improve generalization.

## 📬 Original FT_Transformer Project

https://github.com/yandex-research/rtdl-revisiting-models

