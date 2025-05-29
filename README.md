# Early Detection of Alzheimer's using Deep Learning

This project investigates the effect of DCGAN-based synthetic data augmentation on improving the early-stage classification of Alzheimer's disease using MRI images. A CNN classifier is trained and evaluated with and without GAN-generated images to address the class imbalance and overlap in decision boundaries.

---

## Project Objective

- Classify MRI images into four categories: Non Demented, Very Mild Demented, Mild Demented, and Moderate Demented.
- Address the significant overlap in decision boundaries involving the Very Mild Demented class.
- Use synthetic image generation (DCGAN) to improve classification performance by augmenting the Very Mild Demented class.

---

## Dataset

- **Source**: Augmented Alzheimer MRI Dataset v2 ([Kaggle link](https://www.kaggle.com/datasets/uraninjo/augmented-alzheimer-mri-dataset-v2))
- **Classes**: Non Demented, Very Mild Demented, Mild Demented, Moderate Demented
- Train folder for Training and Val folder for validation

---

## Methodology

1. A CNN classifier is trained on the original dataset as a baseline.
2. A DCGAN is trained using only the Very Mild Demented class images.
3. Five generator models (from different training epochs) are selected based on visual quality and FID score.
4. Each generator produces 500 synthetic images for the Very Mild Demented class.
5. The CNN is retrained separately on the original dataset augmented with each set of synthetic images.
6. Models are evaluated and compared using classification metrics.

---

## Results and Discussion

Only one of the five generators improved the classification performance over the baseline CNN. The other four degraded the results.
- Results show that not all GAN-generated data improves performance.
- Generator selection plays a critical role in the success of synthetic augmentation.
- FID score alone does not guarantee classifier performance improvement.

---


