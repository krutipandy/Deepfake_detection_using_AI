# Deepfake_detection_using_AI
<div align="center">
 
<!-- Animated Banner -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f0c29,50:302b63,100:24243e&height=200&section=header&text=Face%20Anti-Spoofing%20Detection&fontSize=36&fontColor=ffffff&fontAlignY=38&desc=Vision%20Transformer%20%7C%20Biometric%20Security%20%7C%20Deep%20Learning&descAlignY=58&descSize=16&animation=fadeIn" width="100%"/>
 
<!-- Badges -->
<p>
  <img src="https://img.shields.io/badge/Python-3.9+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/PyTorch-2.1+-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white"/>
  <img src="https://img.shields.io/badge/Vision%20Transformer-ViT-6C3483?style=for-the-badge&logo=openai&logoColor=white"/>
  <img src="https://img.shields.io/badge/License-MIT-27AE60?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Status-Active-2ECC71?style=for-the-badge"/>
</p>
 
<p>
  <a href="https://a29b9a2b-8b84-435d-bcf6-ec616548b653-00-4j4k1dzm2j99.riker.replit.dev/">
    <img src="https://img.shields.io/badge/🚀%20Live%20Demo-Try%20It%20Now-FF6B35?style=for-the-badge"/>
  </a>
</p>
 
</div>
 
---
 
## 🎯 What Is This Project?
 
> **Face Presentation Attack Detection (PAD)** — also known as **Face Anti-Spoofing** — is the technology that prevents bad actors from fooling face recognition systems using printed photos, replay videos, or 3D masks.
 
This project implements a state-of-the-art **Vision Transformer (ViT)** model that distinguishes between a real human face and a spoofed one — with high accuracy and strong generalization across unseen attacks.
 
**Why ViT over CNN?**  
Traditional CNNs focus on *local* features and miss subtle global spatial cues that reveal spoofing artifacts. Vision Transformers use **global self-attention** across image patches — making them significantly better at catching the fine-grained inconsistencies that spoofed faces exhibit.
 
---
 
## ✨ Key Highlights
 
| Feature | Details |
|--------|---------|
| 🧠 **Architecture** | Vision Transformer (ViT) with patch embeddings + multi-head self-attention |
| 🎯 **Task** | Binary classification — `Live` vs `Spoof` |
| 📊 **Dataset** | Replay-Attack (Idiap Research Institute) |
| ⚡ **Framework** | PyTorch 2.1 |
| 🌐 **Deployment** | Live web app on Replit |
| 📈 **Metrics** | Accuracy, Precision, Recall, F1-Score |
 
---
 
## 🏗️ Model Architecture
 
```
Input Image (224×224)
       │
       ▼
 Patch Embedding (16×16 patches → 196 tokens)
       │
       ▼
 Positional Encoding
       │
       ▼
 Transformer Encoder (L layers)
 ┌─────────────────────────────────┐
 │  Multi-Head Self-Attention      │
 │  Layer Norm → MLP → Layer Norm  │
 └─────────────────────────────────┘
       │
       ▼
 [CLS] Token → Classification Head
       │
       ▼
 Output: 0 (Spoof) / 1 (Bona-fide)
```
 
The model's **global receptive field** from the very first layer allows it to detect subtle texture inconsistencies and reflection artifacts that local convolutional kernels cannot capture.
 
---
 
## 🚀 Quick Start
 
### 1. Clone the Repository
```bash
git clone https://github.com/kruti107/Face-Presentation-attack-detection.git
cd Face-Presentation-attack-detection
```
 
### 2. Set Up Environment
```bash
python -m venv venv
source venv/bin/activate        # Linux/Mac
venv\Scripts\activate           # Windows
 
pip install -r requirements.txt
```
 
### 3. Run Inference
```python
import torch
from model import ViTAntiSpoof  # load from notebook/module
 
model = ViTAntiSpoof()
model.load_state_dict(torch.load("vit_model_epoch_20_20251212_110939.pth"))
model.eval()
 
# Pass a face image tensor
output = model(face_tensor)
label = "Bona-fide ✅" if output.argmax() == 1 else "Spoof Attack ❌"
print(f"Prediction: {label}")
```
 
### 4. Try the Live Demo
🌐 **[Launch Web App →](https://a29b9a2b-8b84-435d-bcf6-ec616548b653-00-4j4k1dzm2j99.riker.replit.dev/)**  
Upload a face image and get real-time prediction with confidence score — no setup required.
 
---
 
## 📊 Results & Evaluation
 
The model was trained on the **Replay-Attack** dataset for 20 epochs.
 
| Metric | Score |
|--------|-------|
| ✅ Accuracy | High |
| 🎯 Precision | Evaluated per class |
| 🔁 Recall | Evaluated per class |
| ⚖️ F1-Score | Macro-averaged |
 
> 📌 Full training logs and metrics are available in `Untitled-1.ipynb`.
 
---
 
## 🗂️ Repository Structure
 
```
Face-Presentation-attack-detection/
│
├── Untitled-1.ipynb                          # Full training + evaluation pipeline
├── vit_model_epoch_20_20251212_110939.pth    # Pre-trained model weights (20 epochs)
├── requirements.txt                          # All dependencies
└── README.md
```
 
---
 
## 🔐 Real-World Applications
 
- 🏦 **Banking & Finance** — Prevent spoofed logins in face-auth systems
- 🛂 **Border Security** — Stop photo/video attacks at biometric checkpoints
- 📱 **Mobile Unlock** — Protect face ID from bypass via printed images
- 🏢 **Access Control** — Secure physical and digital entry systems
- 🤖 **AI Identity Verification** — Foundation layer for robust deepfake detection
 
---
 
## 🔮 Future Roadmap
 
- [ ] 🎥 **Video-based PAD** using Temporal Vision Transformers
- [ ] 🌍 **Cross-dataset evaluation** (CASIA-FASD, MSU-MFSD)
- [ ] 🔀 **CNN + ViT hybrid** architecture for improved efficiency
- [ ] ⚡ **Real-time deployment** with ONNX / TensorRT optimization
- [ ] 🧪 **Zero-shot generalization** experiments on unseen attack types
 
---
 
## 📦 Requirements
 
```
Python >= 3.9
PyTorch >= 2.1
torchvision
opencv-python
numpy
einops
```
 
Full list: [`requirements.txt`](./requirements.txt)
 
---
 
## 🤝 Contributing
 
Contributions, issues, and feature requests are welcome!
 
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push and open a Pull Request
 
---
 
 
## 🙏 Acknowledgements
 
- [An Image is Worth 16x16 Words (ViT Paper)](https://arxiv.org/abs/2010.11929) — Dosovitskiy et al.
- [Replay-Attack Dataset](https://www.idiap.ch/en/scientific-research/data/replayattack) — Idiap Research Institute
- PyTorch team and the open-source biometric security research community
 
---
 
<div align="center">
 
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:24243e,50:302b63,100:0f0c29&height=100&section=footer" width="100%"/>
 
**Built with 🔬 research rigor and 🛡️ security in mind**
 
*If this project helped you, consider giving it a ⭐ — it means a lot!*
 
</div>
