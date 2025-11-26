# GI Tract Image Segmentation

![header](https://github.com/user-attachments/assets/a6d018ab-db46-4942-a807-a5020771e850)

<p align="right"><sub><i>Image source: <a href="https://www.kaggle.com/competitions/uw-madison-gi-tract-image-segmentation">UW-Madison GI Tract Image Segmentation Competition</a></i></sub></p>

-------------------------------------------------------------------------------------------------------

**📝 Task** : Predict semantic segmentation masks for large bowel, small bowel and stomach across multiple MRI scan slices — identified by case, day, and slice ids.

**📊 Evaluation metric** : Combined metric = 0.6 * (1 - 3D Hausdorff Distance) + 0.4 * Dice Score

ℹ️ Please refer to https://www.kaggle.com/competitions/uw-madison-gi-tract-image-segmentation for more details

-------------------------------------------------------------------------------------------------------

🧠 **Methodology**

- Model Architecture : SegFormer with mit-b3 encoder
  * Classification (presence) head to handle empty masks
- Loss : (Dice + SoftBCE) for segmentation + BCE for presence head
- Input : Used 2.5D image slices to obtain inter-slice context
- Data coherence : Ensured that all slices from the same case-day receive identical augmentations to maintain 3D consistency
- Stabilization : EMA (Exponential Moving Average) weights for final evaluation

-------------------------------------------------------------------------------------------------------

🔨 **Implementation** : Built in Python mainly using PyTorch, Segmentation Models PyTorch (SMP), OpenCV

-------------------------------------------------------------------------------------------------------

📈 **Best Score (Combined metric)**
- Private score : 0.86110 (~ 51% of test data)
- Public score  : 0.86495 (~ 49% of test data) 
- Validation score : 0.86611 (validation data obtained using 80-20 split of train data ensuring equal proportion of empty segmentation mask and non-overlapping case ids)
   - 3D Hausdorff Distance : 0.049
   - Dice Score : 0.739

-------------------------------------------------------------------------------------------------------

**Main contents**
- [GI Tract Image Segmentation notebook](https://github.com/abhivij/GI-Tract-Image-Segmentation/blob/main/gi-tract-image-segmentation.ipynb)
  (The ipython notebook contains images and other details, so please reload in case it does not render properly. Alternatively view the code on Kaggle in the link below)
- [Scores of all runs](https://github.com/abhivij/GI-Tract-Image-Segmentation/blob/main/Scores.xlsx)

-------------------------------------------------------------------------------------------------------

The notebook provided here can be directly accessed and run from :
- [Kaggle - GI Tract Image Segmentation](https://www.kaggle.com/code/abhivij/gi-tract-image-segmentation)
