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

## How to reproduce similar results

Start with downloading all the python notebooks, I used kaggle for it due to the ease of adding dataset directly and free GPU for faster processing. All the respective files are in FINAL folder.
1. cnn-base (3).ipynb: This is the first step of the process, training of a CNN model without any extra augmentation using synthetic images. Trained on images from train folder of the dataset, and validated using val folder of the dataset. Get the baseline models results for inference.
2. dcgan-latest(2).ipynb: This is the second step of process where we build a DCGAN for producing synthetic images of VeryMildDemented class to get more representation for that class in order to get a better decision boundary among overlapping classes. Trained on VeryMildDemented class in train folder of the dataset. Download the saved models and choose best generators with visual inspection and FID score.
3. cnn-model-generator-comparison.ipynb: This takes in 5 best generators selected, adds 500 synthetic images produced of VeryMildDemented class separately to the original dataset per generator, retrains a CNN model to check the effect and results produced by each generator. Save the models created and validate them statistically as well.
4. mcnemar-test.ipynb: This takes in every newly retrained CNN model per generator and Baseline CNN model, check statistically if there is there's a significant difference in performance. We comapre every newly trained model to the baseline validate the performances.
*Every result for validation is shown in respective notebooks itself

---

## Repository Link

The complete source code and materials for this project are available at:  
**https://github.com/KennyPK10/Early-Detection-of-Alzheimers.git**

---
