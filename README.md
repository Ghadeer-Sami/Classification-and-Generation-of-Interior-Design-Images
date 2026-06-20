# Interior Vision: Classification and Generation of Interior Design Images  

---

## Overview
Interior Vision is a dual-track deep learning framework designed for interior design image analysis and generation. The project integrates two complementary models trained on a curated dataset of 4,000 images: a discriminative track for image classification and a generative track for text-to-image synthesis.  
The discriminative track employs an enhanced multi-task ResNet50 model, while the generative track utilizes Stable Diffusion with Low-Rank Adaptation (LoRA). Together, they demonstrate how deep learning can both understand and create realistic interior design concepts.

---

## Project Objectives
- Implement and analyze ResNet50 for multi-task classification of room type and design style.  
- Deploy Stable Diffusion for text-to-image generation using descriptive prompts.  
- Enhance both models through fine-tuning, regularization, and optimization techniques.  
- Evaluate performance using quantitative metrics (accuracy, ROC AUC, CLIP scores) and qualitative visual analysis.  

---

## Dataset
- Source: Interior Design Images & Metadata Dataset (Kaggle)  
- Content: 4,139 images categorized by room type (bathroom, bedroom, kitchen, living room) and design style (boho, industrial, minimalist, modern, scandinavian).  
- Final Cleaned Dataset: 4,000 images after preprocessing.  
- Usage:  
  - Classification: Train CNN models to predict room type and style.  
  - Generation: Create descriptive text prompts for Stable Diffusion fine-tuning.  

Preprocessing Steps:  
- Path correction and cleaning.  
- Prompt generation combining style and room type (e.g., “modern kitchen interior”).  
- Image resizing and RGB conversion.  
- Normalization and augmentation (flip, rotation, crop, color adjustment).  
- Label encoding for classification tasks.  

---

## Methodology

### Discriminative Track – CNN Classification
- Baseline Model: ResNet50 with residual bottleneck blocks and dual classification heads.  
- Improvements:  
  - Data augmentation for diversity.  
  - Dropout regularization (p = 0.4).  
  - Batch normalization in classification heads.  
  - Full backbone fine-tuning for domain adaptation.  
  - Label smoothing (α = 0.1) to improve generalization.  
  - StepLR scheduler and L2 weight decay for stable optimization.  

Performance Impact:  
- Room type accuracy increased from 66% to 74%.  
- Style classification accuracy improved from 54% to 60%.  
- ROC AUC scores rose to 0.9134 (room type) and 0.8518 (style).  

---

### Generative Track – Stable Diffusion with LoRA
- Baseline Model: Latent Diffusion Model with VAE, U-Net, and CLIP text encoder.  
- Improvements:  
  - Increased LoRA rank (r = 16) for richer texture representation.  
  - Cosine annealing learning rate scheduler for smoother convergence.  
  - Extended training steps (from 3,000 to 5,000).  
  - Enhanced prompt engineering with detailed descriptions.  
  - Expanded attention module targeting (query, key, value, output layers).  

Results:  
- Improved stylistic consistency and realism.  
- Better alignment between text prompts and generated images.  
- Reduced generative artifacts and enhanced domain-specific fidelity.  

---

## Results and Evaluation

### CNN Classification
- Room Type Accuracy: 74%  
- Style Accuracy: 60%  
- ROC AUC: 0.9134 (room type), 0.8518 (style)  
- Best Performance: Bathroom and kitchen classes showed highest precision and recall.  
- Challenges: Bedroom and living room overlap visually, making classification harder.  

### Stable Diffusion Generation
- Training Efficiency: LoRA reduced GPU memory usage and accelerated fine-tuning.  
- Qualitative Results: Generated images exhibited realistic lighting, textures, and spatial harmony.  
- Quantitative Evaluation: CLIP scores confirmed improved text-image alignment.  

---

## Key Findings
- Combining discriminative and generative models enhances both understanding and creativity in design domains.  
- CNN improvements led to higher classification accuracy and generalization.  
- LoRA-based diffusion fine-tuning achieved stylistic precision under limited data and hardware constraints.  
- The framework demonstrates the feasibility of deep learning for specialized visual design tasks.  

---

## Future Work
- Expand dataset scale for improved generative diversity.  
- Integrate multi-modal evaluation metrics combining CLIP and human preference scoring.  
- Deploy the system as an interactive web application for design professionals.  
- Explore cross-domain transfer learning for architecture and furniture design.  

---
